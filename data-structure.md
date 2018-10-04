---
description: 此章節將會介紹 JavaScript 的資料型別與資料結構
---

# Data Structure

## 資料結構 {#title}

先前有提到 JavaScript 是個「**動態弱型別**」語言，那奇怪了都是動態弱型別，那還談什麼資料型別？這邊釐清一個觀念：每個程式語言都會有自己的資料結構，有資料結構就有資料型別。這邊將會介紹可以在 JavaScript 中使用的資料結構，以及它們的特性。

### 動態弱型別 {#dynamic-weekly-type}

已經知道了 JavaScript 是弱型別，這代表你可以不用於宣告變數時指定型別，程式在運作時，型別會自動轉換；這也代表你可以以不同的型別重複使用同一個變數。底下的程式範例在 JavaScript 是合法的：

```javascript
var foo = 1;
// foo 現在是數字
var foo = 'meow';
// foo 現在是字串
var foo = true;
// foo 現在是布林值
```

### 原始資料型別 {#primitives-data-type}

JavaScript 有七種資料型別（ECMAScript 標準）：

* 原始型別
  * Boolean
  * Null
  * Undefined
  * Number
  * String
  * Symbol
* Object

> 六個原始資料型別皆不用透過 `new` 實例化就可以直接以其全域物件來建立。

#### Boolean

布林型別用來表示一個實體邏輯，有兩種值：`true`、`false` 。

```javascript
> var isCat = true;
> isCat;
true
```

#### Null

null 表無，在 JavaScript  API 裡要是參照一個沒有型別的物件就會回傳 `null` 。只有一種值：`null` 。

```javascript
// bug 這個變數並未被宣告，且也沒有初始化
> bug;
'ReferenceError: bug is not defined'
// 宣告變數 bug 但不賦值（未初始化）
> var bug;
> bug;
null
// 宣告變數 bug 且給予值 null
> var bug = null;
null
```

#### **Number**

不同於 C/C++ 等語言，JavaScript 的數字型別就只有一種：[**Double（雙精度浮點數）**](https://zh.wikipedia.org/wiki/%E9%9B%99%E7%B2%BE%E5%BA%A6%E6%B5%AE%E9%BB%9E%E6%95%B8)；**而整數並沒有指定的型別**。數字型別除了能代表浮點數以外，還有三個符號值：`+Infinity`、`-Infinity`、`NaN（not-a-number）`。

**語法**

```javascript
> var foo = 1;
> foo;
1
// or
> var foo = Number(1);
> foo;
1
> var foo = Number('1'); // 此舉會將帶入的參數型別轉為數字，值不變
> foo;
1
```

如果建立 `Number` 物件時傳入值不為數字的參數值，將會回傳 `NaN` 

```javascript
> var foo = Number('cat');
> foo;
NaN
```

> API 參照：[https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/Number](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Number)

#### **String**

JavaScript 的字串 `String` 採用 16 進位未宣告「元素」值來表示文字。需要注意的是在 JavaScript 裡並沒有字元 `char` 型別。另外 JavaScript 的字串在創造後是不可修改的，你只能透過操作原字串來產生新字串。

**語法**

```javascript
// 單引號與雙引號在 JavaScript 裡都被視為字串
> var foo = "bar";
> foo;
'bar'

> var foo = 'bar';
> foo;
'bar'

// 也可透過全域的 String 建立字串
> var foo = String('bar');
> foo;
'bar'
```

> API 參照：[https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/String](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/String)

#### Symbol

`Symbol` 一直到 ECMAScript 6 才被規範出來，可作為 `Object` 唯一且不變的鍵值。

#### Object

> 這邊的 Object 為一種資料型別，而非指物件本身。記得在 JavaScript 什麼都是物件。

**語法**

```javascript
// input
var car = {
    'color': 'blue',
    'brand': 'Benz'
}
// or
var car = Object({
    'color': 'blue',
    'brand': 'Benz'
})

console.log(car);
console.log(car.color);

// output
{ color: 'blue', brand: 'Benz' }
'blue'
```

JavaScript 的 `Object` 可視為一個資料集，資料集由許多**值對**組成，一個**值對**由一組**鍵（key）**與其**鍵值（value）**組成。底下範例為一個標準的 Object：

```javascript
{
    'name': 'Neko', // key: value
    'type': 'cat',
    'age': 1 
}
```

> API 參照：[https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global\_Objects/Object](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Object)

### 自訂型別 {#custom-type}

JavaScript 允許你參照現有的型別來建立自訂型別，後面的章節我們將會探討這一塊。

