---
title: JS基礎回顧 - function
tags:
  - function
  - 匿名函式
date: 2020-04-11 11:29:52
categories: JS 基礎回顧
keywords:
- function
- 函式宣告
- 匿名函式
- 回傳值
decription: 有關 function 中的宣告及運作、回傳值，及匿名函式。
---
在看 kuro 大神寫的 [0 陷阱！0 誤解！8 天重新認識 JavaScript！](https://www.tenlong.com.tw/products/9789864344130)（不是業配，這本書很棒）中提到，JavaScript 最核心也最容易被誤用的部份非函式（function）莫屬。我一開始在學 JS 時，碰到函式就覺得非常挫折，因此目前在整理這個筆記時，希望以後可以不用再踩坑？
<!--more-->

## 函式宣告
---

```
function sayhello() {
  console.log ('hi')
}

sayhello()  // 印出'hi'
```

如上面的例子可以看到，函式的宣告及呼叫的運作。

![Image](https://i.imgur.com/HRVJOZV.png)

一個宣告函式主要會包含三個部份：

* 函式的名稱（或是可能沒有名稱）。
* 括號 () 中的部份，是參數。
* 大括號 {} 中的部份，是主要區塊，放重複執行的內容。

### 回傳值

在 function 中還可以使用 return 來取得回傳值，例如：

```
function isPass (score) {
  return (score >= 60)     // 回傳是不是 60 分
}

var myTest = 59;          

if (isPass(myTest)) {      
  console.log('及格')      // 如果就印出及格
} else {
  console.log('不及格')    // 如果不是就印出不及格，最後結果是不及格
}
```

## 匿名函式
---

在上一個函式中的寫法是：

```
function isPass (score) {
  return (score >= 60)   
}
```

而在另一種的寫法，透過`變數名稱 = function ([參數] {...})`,將一個函式透過 = 指定給某個變數：

```
// function 後面沒有名稱
var isPass = function (score) {
  return (score >= 60)
}
```

因為在變數型別中，除了基本型別以外的都是**物件型別**，所以可以被呼叫，自然也可以透過變數存入。

也由於在這個例子中，function 後面沒有名稱，所以是**匿名函式**。

如果要替它加上名稱也是可以，例如：

```
var isPass = function func(score) {
  return (score >= 60)
}
```

但是要注意的是，這個 func 只在**自己函式範圍**有效，看以下的例子：

```
var isPass = function func (score) {
  console.log(typeof func);  // 使用 typeof 可以判斷型別
  return (score >= 60)
}

console.log(typeof func);
```

上面的結果，第一個 typeof 判斷是 function，第二個則是出現 undefined，func 一旦不在自己函式範圍內，就不存在了。

不過如果想要取得這個 function 的名稱，也可以透過自定義的變數名稱，例如：

```
var isPass = function func (score) {
  console.log(typeof isPass);
  return (score >= 60)
}

console.log(typeof isPass)
```

2 個 console.log 結果都會顯示 function。