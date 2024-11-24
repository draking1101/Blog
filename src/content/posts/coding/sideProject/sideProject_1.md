---
title: 網頁練習作品 1 - 圖片輪播
published: 2024-11-23
description: '練習製作簡單的圖片輪播功能'
image: '/posts/coding/sword_girl.jpg'
tags: [SideProject]
category: '程式設計'
draft: false 
lang: ''
---
# 文章簡介

輪播功能是參考了別人的作品來學習，並修正了作品中輪播圖片會重疊的問題

輪播檔案 : [點我前往](<https://github.com/draking1101/CodeNote/tree/main/%E7%B7%B4%E7%BF%92%E6%AA%94%E6%A1%88/%E5%85%B6%E4%BB%96/%E8%BC%AA%E6%92%AD>)

參考資料 : [點我前往](<https://vocus.cc/article/660bb860fd89780001a0beca>)


# 輪播架構

- **輪播框架** : 基本上等於輪播區域的位置，除非想再加其他東西進來。
- **輪播區域** : 包含所有要輪播的圖片。
- **輪播圖片** : 輪播區內的圖片，每張圖自成一個容器。
- **輪播按鈕** : 手動觸發輪播。

# 圖片重疊問題

如果圖片不是全覆蓋的( 比如有透明背景的png檔 )，原程式會發生圖片重疊問題。這是因為輪播可以連續觸發沒有冷卻，因此我的解決方法是添加事件監聽器 `transitionend`。
- 為每個圖片元素監聽 `transitionend` 事件。
- 當動畫過渡效果完成時，事件會被觸發，然後將 `isSliding` 設為 `false`。
- 這樣可以確保動畫結束後，才允許下一次滑動。
```js
slide.forEach((slideElement) => {
    slideElement.addEventListener("transitionend", () => {
        logText.style.color = 'black';
        logText.innerText = `${hint}輪播結束`;
        isSliding = false;
    });
});
```

# 輪播功能

左右邊的按鈕會觸發輪播，按鈕功能邏輯如下
## 1. 檢查輪播狀態 ( 是否正在輪播中 )
   - 如果正在輪播，則停止，避免重複輪播使圖片重疊
   - 如果沒再輪播，則繼續。

## 2. 更新 `slideIndex` 來改變當前顯示的圖片
   - `slideIndex` : 當前的圖片的index
```js
const slideLength = slide.length; // 輪播的圖片數量
slideIndex = (slideIndex + 1) % slideLength;
```

## 3. 透過更新圖片容器的 `class` 來改變上/下一張圖片的位置，讓圖片輪替

- `sliderPrevIndex` : 上一張圖片的index
- `sliderNextIndex` : 下一張圖片的index

```js
function updateClasses() {
    // 更新PrevIndex
    if (slideIndex === 0) {
        // slideIndex = 0時代表當前圖片為第一張，則上一張圖片的Index = 總數量-1，也就是最後一張
        sliderPrevIndex = slideLength - 1;
    } else {
        sliderPrevIndex = slideIndex - 1;
    }

    // 更新NextIndex
    if (slideIndex === slideLength - 1) {
        // slideIndex = 總數量-1 時代表當前圖片為最後一張，則下一張圖片的Index = 總數量0，也就是第一張
        sliderNextIndex = 0;
    } else {
        sliderNextIndex = slideIndex + 1;
    }

    // 重置class，確保class給對
    slide.forEach((i) => {
        i.classList.remove("active", "prev", "next");
    });

    slide[slideIndex].classList.add("active");
    slide[sliderPrevIndex].classList.add("prev");
    slide[sliderNextIndex].classList.add("next");
}
```
`CSS`
```css
.active {
  left: 0%;
  z-index: 10; // 確保當前的圖片在最上層
}

.prev {
  left: -100%; // 確保上一圖片在左邊
}

.next {
  left: 100%; // 確保下一張圖片在右邊
}    
```

# 備註
## CSS
- `overflow: hidden` : 用來隱藏非當前顯示的圖片

## `SCSS` 安裝方式
1. 輸入以下命令安裝 Sass
```sh
npm install -g sass
```
2. 安裝完成後，可以輸入以下命令來檢查 `Sass` 是否安裝成功
```sh
sass --version
```
3. 使用 `Sass` 編譯 `SCSS` 文件

假設你有一個名為 `styles.scss` 的 `SCSS` 文件，並且你想要將它編譯成 `styles.css`，可以使用以下命令：
```sh
sass styles.scss styles.css
or
sass <folder/>/<scss_file_name/> <folder/>/<css_file_name/>
```
如果希望 `SCSS`自動檢測 `SCSS` 文件的變化並自動重新編譯，則可以使用 `--watch` 參數：
```sh
sass --watch styles.scss:styles.css
or
sass --watch <folder/>/<scss_file_name/>:<folder/>/<css_file_name/>
```