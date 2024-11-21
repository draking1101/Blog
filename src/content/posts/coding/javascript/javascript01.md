---
title: JavaScript 1
published: 2024-11-21
description: '理解 JavaScript 的基本語法與運作方式'
image: '/posts/coding/sword_girl.jpg'
tags: [JavaScript]
category: '程式設計'
draft: false 
lang: ''
---
## 目標
理解 JavaScript 的基本語法與運作方式。

## 學習內容

### 1. JavaScript 介紹
JavaScript 是網頁開發中不可或缺的語言，主要用於實現網頁的互動效果。它是一種基於事件驅動、輕量且解釋執行的語言，特別適合於開發用戶端腳本來增強用戶體驗。

- 語言特性：動態、弱類型、基於原型
- **弱類型**：JavaScript 是一種弱類型語言，這意味著變量的類型是可以改變的，並且在運算過程中可以自動進行類型轉換。這種靈活性使得 JavaScript 在編寫時相對容易上手，但同時也帶來了一些可能的陷阱，例如隱式轉換導致的預期外的結果。
  
  ```javascript
  let value = '5'; // 當前 value 是字符串類型
  value = value * 2; // JavaScript 會自動進行隱式轉換，結果 value 為數字 10
  console.log(value); // 10
  ```
  這種自動類型轉換在某些情況下可能會導致混淆，因此在需要精確控制的情況下建議使用顯式類型轉換。

- 應用場景：DOM 操作、瀏覽器事件處理、API 調用

### 2. 變量與常量
在 JavaScript 中，可以使用 `let`、`const` 和 `var` 來聲明變量和常量：

- **`let`**：用於聲明變量，可以重新賦值。
- **`const`**：用於聲明常量，一旦賦值則不能改變。
- **`var`**（不推薦）：舊版本用法，具有更寬鬆的作用域，容易導致意想不到的問題。

```javascript
let age = 18;
const name = '姬';
var oldValue = 42;
```

### 3. 數據類型與轉換
JavaScript 提供多種數據類型，可以分為基本型別和引用型別：

- **基本型別 ( Primitive Type )**：
  - **字符串 (String)**
  - **數字 (Number)**
  - **布林值 (Boolean)**
  - **未定義 (Undefined)** : 空值，被宣告後沒給予值，會被預設為undefined
  - **空 (Null)** : 空值，與undefined差別在於這是被刻意給予空值的
  - **符號 (Symbol)**

  ```javascript
  let str = 'Hello, World'; // 字符串
  let num = 42; // 數字
  let isAdult = true; // 布爾值
  let emptyValue = null; // 空
  let notDefined; // 未定義
  let uniqueId = Symbol('id'); // 符號
  ```

- **<u>參考 / 物件</u> 型別( Reference / Object Type )**：
  - **對象 (Object)**
  - **數組 (Array)**
  - **函數 (Function)**

  ```javascript
  let person = { name: '姬', age: 28 }; // 對象
  let numbers = [1, 2, 3, 4]; // 數組
  function greet() { // 函數
      console.log('Hello!');
  }
  ```

數據類型的轉換包括顯式轉換和隱式轉換。

```javascript
let number = '42';
let convertedNumber = Number(number); // 顯式轉換為數字
let implicitConversion = '5' * 2; // 隱式轉換，結果為數字 10
```

### 4. 基本運算符與條件語句

#### 運算符
- **算術運算符**：`+`、`-`、`*`、`/`、`%`
  ```javascript
  let a = 10;
  let b = 3;
  console.log(a + b); // 13
  console.log(a - b); // 7
  console.log(a * b); // 30
  console.log(a / b); // 3.333...
  console.log(a % b); // 1
  ```

- **比較運算符**：`==`、`===`、`!=`、`!==`、`>`、`<`、`>=`、`<=`
  ```javascript
  let x = 5;
  let y = '5';
  console.log(x == y);  // true (值相等，類型不比較)
  console.log(x === y); // false (值相等，但類型不同)
  console.log(x != y);  // false (值相等)
  console.log(x !== y); // true (類型不同)
  console.log(x > 3);   // true
  console.log(x <= 5);  // true
  ```

#### 條件語句
- **`if-else`**：用於根據條件執行不同的代碼塊。
- **`switch`**：用於在多個條件中選擇一個。

```javascript
let age = 20;

if (age >= 18) {
    console.log('成年');
} else {
    console.log('未成年');
}

let color = 'red';
switch (color) {
    case 'red':
        console.log('顏色是紅色');
        break;
    case 'blue':
        console.log('顏色是藍色');
        break;
    default:
        console.log('未知顏色');
}
```

## 實踐練習
你可以嘗試撰寫一些小程式來加深理解，比如以下這個判斷年齡是否成年的條件判斷程式：

```javascript
function isAdult(age) {
    return age >= 18 ? '成年' : '未成年';
}

console.log(isAdult(16)); // 輸出：未成年
console.log(isAdult(20)); // 輸出：成年
```

通過這樣的練習來熟悉基本語法和條件判斷，逐步提升對 JavaScript 的掌握。
