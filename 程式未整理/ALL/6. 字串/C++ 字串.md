---
tags: C++ 
aliase: 
created: 2023-02-21 16:58
modified: 星期二 21日 二月 2023 16:58:54
---

# C++ 字串
***
>[!info]+
>在C++中String是一種class而非Data type

# String vs charArr
| 比較   | string | charArr |
|:-----|:-------|:--------|
| 存取速度 | 慢      | 快       |
| +運算  | 可      | 否       |
| 內存   | 動態     | 靜態      |
| 衰變   | 否      | 會       |  
衰變可參考:[[C 陣列#衰變]]

char array 是一個字符類型的數組，使用字符數組可以方便地存儲和處理字符串，但需要**手動管理**內存<u>分配</u>和<u>釋放</u>，而且不能直接進行字符串的*比較、連接、截取*等操作。

String 是 C++ 標準庫中的一個類，通過使用 String 對象可以更加方便地處理字符串。 String 類實現了自動內存管理，能夠自動調整內存大小，也提供了許多操作字符串的函數，如比較、連接、截取等等。此外，使用 String 對像也可以避免 char array 中的一些內存錯誤，例如*緩衝區溢出*等。

總的來說，String 對象更加方便和安全，可以使用更多的字符串操作函數，而 char array 則更靈活，可以更加自由地控制內存和實現一些底層操作。選擇哪個取決於具體的需求和應用場景。

---
# 字串處理
## 字串連接
1. +
2. str.append(string)
3. str.insert(pos, string)
```cpp linenos title:"連接"
string str1 = "Helo, "; //"Helo, "
str1.append("world");//"Helo, world"
str1 += "!";//"Helo, world!"
str1.insert(1, "l");//"Hello, world!"
```

## 字串賦值
>[!success]+
>在 C++ 中，字符串字面值 (string literals) 在被創建時會被存儲在**字符串池 (string pool)** 中，而字符串池中的字符串對像是**不可變的 (immutable)**，也就是說，它們的值無法被改變。

```java
String a = "asd";  // 在string pool 中創建 "asd"
```

Q: 為什麼下列程式碼輸出為true
```java
String a = "asd";
String b = "asd";
System.out.println(a==b);
```

>[!note]- Ans
>a存的是ref，b也是，它們都指向string pool 裡的"asd"

>[!question]+
`String b2 = "asdasd"; `
>Q: b2 是常量嗎？

變量 b2 存儲的是字符串池中的一個對象*引用*，而這個對像是不可變的。雖然變量 b2 可以被重新賦值，但是字符串 "asdasd" 是一個常量。

Q: b2 存在記憶體的哪個位置？是在stack內嗎？
變量b2中存儲的實際上是對常量池中字符串對象的*引用*，而不是字符串對象本身。因此，*b2本身是一個變量*，它在堆棧中分配了內存，但其值引用了常量池中的字符串對象。

Data:
你的意思是字串"asdasd" 在String pool 新增， b2 在Stack里分配空間，b2存的是"asdasd"在String pool裡的位置這樣嗎？

是的，您的理解是正確的。當Java編譯器看到字面值字符串時，它會將字符串添加到String Pool中。當您聲明一個String變量並使用該字面值初始化它時，它將被初始化為String Pool中的對象的引用。在Stack中，變量存儲的是對String對象的引用。

---
## 字串比較
>[!info]+
>比較字串不該使用`==`，應該使用str.equals(str)來比較字串，`==`比較的是reference

```java linenos
String a = "asd";
String b = new String("asd");
System.out.println(a==b);
System.out.println(a.equals(b));
```
```result
false
true
```

## 數字 字串轉換
```java linenos
//字串轉數字
int a = Integer.parseInt("123");

//數字轉字串
String b = Integer.toString(123);
String c = String.format("%d", 10);
```

- Double.parseDouble(str)

## 字串替代

使用 replace() 函數：可以用一個 string 替換另一個 string 中指定的子串。
string str1 = "Hello, world!";
string str2 = "everyone";
str1.replace(7, 5, str2); // 用 str2 替換 str1 中從第 7 個字符開始的 5 個字符
這些方法都可以用來連接多個字串。

---
# 字元陣列處理


---
# 字串模組
## format
>[!info]+
>與printf使用方式相同，但**回傳String**

```java linenos
int a = 10;
String b = String.format("%d", 10);
```
