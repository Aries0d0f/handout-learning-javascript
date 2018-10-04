---
description: 本章節將解釋在 JavaScript 下宣告變數的方法與規則
---

# Declarations

## 宣告變數 {#title}

### 基礎語法 {#basic}

> 說 JavaScript 是個學人精再適合不過了。JavaScript 整體設計上參考了 Java、Python、Perl 等先輩，要是你先前學習過其他程式語言，可能會在學習 JavaScript 過程中看到似曾相識的語法。

JavaScript 是個「**區分大小寫**」的程式語言，並且採用 **Unicode（萬國碼）**作為其編碼方式。也就是說，你將可以用任何 Unicode 字元來編寫你的程式。以下範例是合法的 JavaScript 程式：

```javascript
> var 喵 = 'cat';
> 喵;
'cat'
```

JavaScript 是區分大小寫的，所以要注意變數名稱的使用：

```javascript
> var foo = 1;
> Foo;
'ReferenceError: Foo is not defined'
```

在 JavaScript 裡通常以**分號 `;`** 作為每行指令的分隔，空格、Tab 與換行符號皆被視為空白處理。不過與 C/C++、Java 等程式語言不同，編寫 JavaScript 程式時並不強制你要在每行結尾加上分號，也就是說以下的語法也是正確的。

```javascript
> var 喵 = 'cat'
> 喵
'cat'
```

### 註解 {#comments}

```javascript
// 單行註解範例

/*
    多行註解範例
    多行註解範例
*/
```

### 變數與常數 {#variable-and-constant}

JavaScript 有三種變數宣告的方式：

* `var` ：宣告一個**可隨意更改其內容**的變數
* `let` ：宣告一個**可隨意更改其內容**的**區塊區域**變數
* `const` ：宣告一個**唯讀**的**不可變**常數 

好我知道有人已經聽到目煞煞，`var` 與 `const` 還好理解（一個可變一個不可變），那天外殺出一個 `let` 又與 `var` 差在哪？光說無益，請觀察底下兩組範例與輸出結果：

```javascript
// input
var x = 1;

if (x === 1) {
    var x = 2;
    console.log('x_1', x);
}

console.log('x_2', x);

// output
x_1 2
x_2 2
```

```javascript
// input
let x = 1;

if (x === 1) {
    let x = 2;
    console.log('x_1', x);
}

console.log('x_2', x);

// output
x_1 2
x_2 1
```

> 有沒有發現什麼不一樣的地方呢？沒發現代表你太累了，起來走走喝杯咖啡再繼續吧

透過兩個範例可以明顯觀察到，`let` 與 `var` 最大的不同也是唯一的不同就在於 `let` 是**區域變數**，而 `var` 則是**全域變數**。在第四行至第七行範圍內的 `if` 條件式形成了一個封閉的獨立區域，我們把它叫做**閉包**。在這個區域內使用 `let` 宣告的變數只活在閉包的範圍內，並不會影響到一開始宣告的變數值。你可以想像成是你在夢裡中了大樂透，但醒來的現實生活中你的戶頭還是月底吃土的狀態。

