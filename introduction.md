---
description: >-
  這章節將提到 JavaScript
  基礎架構與概念，以及如何運用於網頁上。這章可能出現一些看似深奧的名詞，不過不用慌張，這些概念都會做解釋，能理解這部分的架構介紹將會對於往後學習
  JavaScript 有很大的幫助。
---

# Introduction

## 基礎架構 {#structure}

![JavaScript Logo](.gitbook/assets/javascript-36f5949a45%20%281%29.png)

> **JavaScript** 是一種可以運行於**宿主環境（直譯器）**的**解釋執行**程式語言，現也支援**即時編譯（JIT**），基於**原型**構成（**Prototype-based Language**）、採用**動態弱型別**且支援 **Object-oriented programming（物件導向編程）**、**Imperative programming（指令式程式設計）**、**函數程式設計（Functional Programming）**。

以上廢話沒有全看懂也沒關係，不過目前為止你該搞懂的重點有三：

* JavaScript 是**直譯**語言
* JavaScript 是 **Prototype-based Language**
* JavaScript 為**動態弱型別**語言

看完還是沒有很懂？

### 直譯語言 {#literal-language}

首先，講講**直譯**語言吧。

與**編譯**語言不同，採用編譯語言的程式是先將程式透過**編譯器**編譯為機械碼（或中間碼）後再加以執行，而直譯語言則是透過**直譯器**將程式碼逐句直譯成機械碼並執行（**解釋執行**）。直譯語言可以更方便的進行除錯，開發起來也可以更彈性更快速；但直譯語言也有個大缺點：執行效率不如編譯語言。

打個比方好了，編譯語言像是先請翻譯者將整本寫好的英文小說翻譯成中文再讓你讀，而直譯語言則是現場英文演說搭配中文口譯給你聽。而 JavaScript 是目前最廣泛被用於瀏覽器上的程式語言，瀏覽器內想當然而就內建了 JavaScript 的直譯器了。

### Prototype-based Language

再來讓我們看看什麼是**原型（Prototype）**。

![](.gitbook/assets/1-ndbfampflmssikfmlxwivq.jpeg)

這邊要先講一些物件導向的基礎概念，否則你這段會鴨子聽雷。

#### **OOP（物件導向編程）的三個易混淆名詞**

* **Class**：被用來定義 **Object** 的藍圖，包含**動作（Operation）**與**資料（Data）**兩部份。
* **Object**：包含許多**動作（Operation）**，且儲存這些操作產生的**狀態（State）**變化。
* **Instance**：透過參照 **Class** 來創建的 **Object** 稱為 **Instance**。可將 **Object** 與 **Instance** 視為同一種東西。

#### **OOP（物件導向編程）精神**

其實整個偉哉 OOP 就一句話，**資料跟動作在一起**。

就是個工具箱的概念！這邊簡單舉個例子：假設一個**標準工具箱規定（Class）**至少應該要有**螺絲起子（Operation）**、**槌子（Operation）**、**螺絲（Data）**、**釘子（Data）**，你可以購買廠商**依規定製作的工具箱（Object／Instance）**來使用，透過**錘子（Operation）**來**釘釘子（State）**。物件導向程式設計講求對於任何物件內的資料，都應透過包含於物件內的動作來操作，爾後儲存其狀態。

物件導向的語言通常都需要一個萬靈丹來解決物件之間**繼承（Inherit）**與**參照（Reference）**的問題（建立關係樹規則）。與 Java 不同，JavaScript  並沒有 class 這個上帝來創造萬物，在 JavaScript 的小宇宙裡只有 Object、Instance。那怎麼辦呢？誰來訂定規則？於是 JavaScript 使用**原型（Prototype），**物體創建，複製或繼承通通是透過 Prototype 完成。

**原型（Prototype）**是一種 JavaScript 的特性，整個 JavaScript 語法都與**原型**息息相關。有聽過「先有雞，還是先有蛋」這個問題嗎？這裏不討論哲學答案，不過在 JavaScript 的世界答案絕對是「先有 Prototype」。Prototype 就像是基因，雞就是個 Object，而雞生下的雞蛋就是那個 Instance 拉！不同的動物之間基因不一樣，所以 JavaScript 裡不同 Object 的 Prototype 也是不一樣的。

在 JavaScript 的國度**什麼都是物件**，而許多物件關係經由 **Prototype** 串接起來，就是**原型鍊（Prototype Chain）**。這部分我們會在後面的章節做更深的討論。

### **動態弱型別** {#dynamic-weekly-type}

最後，我們來講 JavaScript 的**動態弱型別**。

> 你說為什麼要談完了這些讓我一頭霧水的東西才開始講 JavaScript 的型別？因為要是沒有先了解 Prototype 的概念，到後面你會一直問為什麼。

先講講什麼是「動態弱型別」。要了解動態弱型別，我們必須先將這個字重新拆解為「**動態型別**」與「**弱型別**」

#### 動態型別

如果一個程式語言對變數的型別檢查，可在不測試執行期運算式是否等價的情況下進行，該語言即為**靜態型別**：換句話說，程式只需在編譯期進行獨立的型別檢查，而無需理會執行階段的狀態；反之則為**動態型別**。

蛤？你說為什麼要在執行時期檢查型別？一個程式語言在被解析（包含**編譯、直譯**）時，會將程式碼切成小塊後予以型別標記，如果此程式語言支援執行期時調度原先的型別標記，那就需要在執行時期反覆進行型別檢查。**動態型別**允許你在程式碼中宣告變數時不需指定型別，而是透過其「**推斷型別**」的功能（也被稱為**鴨子型別**）透過運算式行為來推斷其型別。

> **鴨子型別**
>
> 「當看到一隻鳥走起來像鴨子、游泳起來像鴨子、叫起來也像鴨子，那麼這隻鳥就可以被稱為鴨子。」其關注點在於物件的行為，能作什麼；而不是關注物件所屬的類型。

#### 弱型別

**強型別**與**弱型別**別並沒有非常明確的定義，但主要描述程式語言對於混入不同資料型別的值進行運算時的處理方式。**強型別**的語言遇到函式引數型別和實際叫用型別不符合的情況經常會直接出錯或者編譯失敗；而**弱型別**的語言常常會實行**隱式轉換**，或者產生難以意料的結果（Bug）。

JavaScript 是個動態的弱型別語言，這也意味著使用 JavaScript 編程時如果不以嚴謹、系統化邏輯的方式進行編程，將會對開發產生許多不必要的麻煩。

關於 JavaScript 資料型別的詳細介紹請看 [Data Structure](https://handouts.aries0d0f.me/javascript-handout-basic/data-structure) 章節

## 在 HTML 中嵌入或引用你的 JavaScript {#use-js-in-html}

網頁中，一個標準的 JavaScript 程式可以分為**內部嵌入腳本**與**引用外部檔案**兩種。

### **內部嵌入腳本** {#internal-embedded}

直接使用 HTML 的 `<script>` tag 嵌入於 HTML：

```markup
<script>
    ...
</script>
```

### **引用外部檔案** {#external}

使用 `<script src="` 腳本路徑 `">` 引入腳本至 HTML：

```markup
<script src="/path/to/scriptfile.js"></script>
```

一個標準的 JavaScript 腳本使用 `.js` 作為其副檔名。

