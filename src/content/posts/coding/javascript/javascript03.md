---
title: JavaScript 3
published: 2024-11-21
description: '物件與DOM操作'
image: '/posts/coding/sword_girl.jpg'
tags: [JavaScript]
category: '程式設計'
draft: false 
lang: ''
---
## 目標
掌握JavaScript操作網頁的基本能力。
## 1. 物件與陣列的操作

### 物件 (`Object`) 和陣列 (`Array`)

物件和陣列是 JavaScript 中非常重要的資料結構。以下是一些常見的操作方法：

#### 物件的操作

- **新增屬性**：
  ```javascript
  let person = {};
  person.name = 'Alice';
  person.age = 25;
  console.log(person);  // { name: 'Alice', age: 25 }
  ```

- **刪除屬性**：
  ```javascript
  delete person.age;
  console.log(person);  // { name: 'Alice' }
  ```

#### 陣列的操作

- **`push()` 與 `pop()` 的功能**：
  - `numbers.push(4)`：將元素 `4` 加入到 `numbers` 陣列的末尾。並返回新陣列的長度
  - `numbers.pop()`：移除並返回 `numbers` 陣列的最後一個元素。
  - 
  - **例子**：
    ```javascript
    let numbers = [1, 2, 3];
    let length = numbers.push(4);  // numbers 變成 [1, 2, 3, 4]
    console.log(length);  // 返回 4，因為陣列的長度變成了 4
    console.log(numbers.pop());  // 返回 4
    console.log(numbers);        // numbers 變成 [1, 2, 3]
    ```

- **新增元素**：
  ```javascript
  let numbers = [1, 2, 3];
  numbers.push(4);
  console.log(numbers);  // [1, 2, 3, 4]
  ```

- **刪除元素**：
  ```javascript
  numbers.pop();
  console.log(numbers);  // [1, 2, 3]
  ```

- **修改元素**：
  ```javascript
  numbers[1] = 20;
  console.log(numbers);  // [1, 20, 3]
  ```

- **查找元素**：
  ```javascript
  let index = numbers.indexOf(20);
  console.log(index);  // 1
  ```

## 2. DOM（Document Object Model）操作

### 選取元素

- **使用 `document.querySelector`**
  ```javascript
  const heading = document.querySelector('h1');
  console.log(heading);
  ```

- **使用 `document.getElementById`**
  ```javascript
  const button = document.getElementById('myButton');
  console.log(button);
  ```

### 修改元素內容與屬性

- **修改內容**：
  ```javascript
  heading.textContent = 'Hello, World!';
  ```

- **修改屬性**：
  ```javascript
  button.setAttribute('disabled', 'true');
  ```
  範例
    ```html
    <body>
    <button id="myButton">點擊我</button>
    <script>
        const button = document.getElementById('myButton');

        // 設定按鈕為禁用（disabled）
        button.setAttribute('disabled', 'true');

        // 這裡就算按下按鈕也無法觸發任何事件，因為它已經被禁用
        button.addEventListener('click', () => {
        alert('這個按鈕被點擊了！');
        });
    </script>
    </body>
    ```

### 事件處理

- **按鈕點擊事件**：
  ```javascript
  button.addEventListener('click', () => {
    alert('按鈕被點擊了！');
  });
  ```

## 3. 實踐練習

### 在網頁上動態顯示數據

- **目標**：當按下按鈕時顯示一段文字。

    ```html
    <button id="showTextButton">顯示文字</button>
    <p id="text"></p>
    <script>
        const showTextButton = document.getElementById('showTextButton');
        const text = document.getElementById('text');
        
        showTextButton.addEventListener('click', () => {
        text.textContent = '這是動態顯示的文字。';
        });
    </script>
    ```
