---
title: JavaScript 2 - 流程控制與函數
published: 2024-11-21
description: '流程控制與函數'
image: '/posts/coding/sword_girl.jpg'
tags: [JavaScript]
category: '程式設計'
draft: false 
lang: ''
---
# JavaScript 筆記
## 目標
能夠寫出簡單的程式邏輯。

## 1. 循環
循環結構讓你能夠重複執行一段代碼，直到達到某個條件為止。常見的循環有以下幾種：

### for 循環
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);  // 輸出 0, 1, 2, 3, 4
}
```
這個循環從 `i = 0` 開始，直到 `i < 5` 為止，並在每次循環後 `i` 增加 1。

### while 循環
```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;  // 輸出 0, 1, 2, 3, 4
}
```
`while` 循環會一直執行，直到條件變為 `false`。

### do...while 循環
```javascript
let i = 0;
do {
    console.log(i);
    i++;
} while (i < 5);  // 輸出 0, 1, 2, 3, 4
```
`do...while` 循環會先執行一次代碼塊，然後再檢查條件是否成立，直到條件為 `false`。

## 2. 函數的定義與調用

### 普通函數
```javascript
function sum(a, b) {
    return a + b;
}
console.log(sum(3, 4));  // 輸出 7
```

### 箭頭函數
箭頭函數 `(() =>)` 是簡化函數定義的一種方式，通常用於簡單的邏輯中。
```javascript
const sum = (a, b) => a + b;
console.log(sum(3, 4));  // 輸出 7
```

## 3. 作用域與閉包

### 作用域
變數的作用範圍決定了它可以在代碼中被訪問的區域。主要有：

- **全局作用域**：在程式的任何地方都能訪問。
- **局部作用域**：只在函數內部有效。

```javascript
let a = 10;  // 全局變數
function example() {
    let b = 20;  // 局部變數
    console.log(a, b);
}
example();  // 輸出 10 20
// console.log(b);  // 錯誤，因為 b 在函數外部不可訪問
```

### 閉包
閉包是指函數可以記住並訪問它被創建時的作用域。
```javascript
function outer() {
    let a = 10;
    return function inner() {
        console.log(a);
    };
}
const closure = outer();
closure();  // 輸出 10，因為 inner 函數「記住」了 outer 函數的作用域
```

## 4. 實踐練習：計算任意數組和的函數

實踐目標是寫一個函數來計算任意數組的和，使用循環來遍歷數組中的每一個元素。
```javascript
function sumArray(arr) {
    let sum = 0;
    for (let i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    return sum;
}
console.log(sumArray([1, 2, 3, 4, 5]));  // 輸出 15
