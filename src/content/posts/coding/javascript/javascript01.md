---
title: JavaScript01 - 資料型別
published: 2024-11-19
description: 'JavaScript的資料型別'
image: '/posts/coding/sword_girl.jpg'
tags: [JavaScript]
category: '程式設計'
draft: false 
lang: ''
---
# 基本型別（Primitive Types）
有 6 + 1種資料型別是基本型別：`String`、`Boolean`、`Number`、`BigInt`、`Undefined`、`Null` 與 EC6加入的 `Symbol` 。

| Type      | Description                                                                                   | Example                         |
|-----------|-----------------------------------------------------------------------------------------------|---------------------------------|
| String    | 代表文本字串。                                                                               | `"Hello, world"`, `'JavaScript'`|
| Boolean   | 代表布林值，只有兩個可能的值：`true` 和 `false`。                                             | `true`, `false`                 |
| Number    | 代表所有數字，包括整數和浮點數。                                                             | `42`, `3.14`                    |
| BigInt    | 表示大整數，可以處理超過 `Number` 類型可表示的範圍（ES2020+）。                                | `123n`, `BigInt(1234567890123)` |
| Undefined | 當一個變數被宣告但未賦予任何值時，該變數的值就是 `undefined`。                                | `let a; // a 是 undefined`      |
| Null      | 代表空值或空對象，通常用來表示某個值是刻意的“空”或“無”。                                     | `let b = null;`                 |
| Symbol    | 表示唯一的標識符，常用來創建對象的唯一屬性鍵（ES6+）。                                         | `Symbol('desc')`                |


| Type           |`typeof` return value| Object wrapper |
|----------------|---------------------|----------------|
| String         | "string"            | String         |
| Boolean        | "boolean"           | Boolean        |
| Number         | "number"            | Number         |
| BigInt         | "bigint"            | BigInt         |
| Undefined      | "undefined"         | N/A            |
| Null           | "object"            | N/A            |
| Symbol         | "symbol"            | Symbol         |

## Object wrapper 

JavaScript 提供了一組對應的對象類型，稱為“Object wrapper”。當對一個基本型別調用方法時，JavaScript 會在背後會自動進行轉換，使得可以像對待對象那樣操作這些值。這種自動轉換的過程叫做 “自動裝箱”（autoboxing）

以下是每種基本型別和它們的對應 Object wrapper 類型：
- `Boolean`
```js
true.toString() 會被轉換為 (new Boolean(true)).toString()
```
- `Number`
```js
(123).toFixed(2) 會被轉換為 (new Number(123)).toFixed(2)
```
- `String`
```js
'hello'.toUpperCase() 會被轉換為 (new String('hello')).toUpperCase()
```
- `Symbol`
```js
Symbol('desc').toString() 會被轉換為 (new Symbol('desc')).toString()
```
- `BigInt`
```js
(123n).toString() 會被轉換為 (new BigInt(123n)).toString()
```
- `Null` 和 `Undefined`
    - `Null` 和 `Undefined` 沒有對應的 Object wrapper。
    - 它們是特殊的基本型別，在 JavaScript 中沒有對應的構造函數，也不能使用對象的方式來包裝它們。因此對 `null` 和 `undefined` 調用方法會報錯。
# 參考型別（Reference Types）
除了基本型別外都可以歸類在參考型別。

| Type       | `typeof` return value | Description                               |
|------------|-----------------------|-------------------------------------------|
| Object     | "object"              | 基本屬性上是一組Key跟value的組合而成        |
| Array      | "object"              | 與物件差別為有序集合，使用`[]`索引值(index)，由0開始。   |
| Function   | "function"            | 可調用的函數                              |
| Date       | "object"              | 表示日期和時間的對象                       |
| RegExp     | "object"              | 正則表達式，用於匹配字串模式                |
| Error      | "object"              | 錯誤對象，用於處理異常                     |
