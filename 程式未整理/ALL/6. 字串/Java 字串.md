---
tags: Java
aliase: string
created: 2023-01-03 12:18
modified: 星期四 12日 一月 2023 14:43:59
---

# Java 字串
***
>[!info]+
>在Java中String是一種class而非Data type

>[!success]+
>在Java中字串加法會默認將其他型態轉為String

---

# C++ String vs charArr


# 字串處理
## 字串連接
>[!info]+
>在Java中默認使用運算子`+`做連接，並且其他類型與String做加法會默認為字串相接

## 字串賦值
>[!success]+
>在 Java 中，字符串字面值 (string literals) 在被創建時會被存儲在**字符串池 (string pool)** 中，而字符串池中的字符串對像是**不可變的 (immutable)**，也就是說，它們的值無法被改變。

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

---

# 字串模組
## format
>[!info]+
>與printf使用方式相同，但**回傳String**

```java linenos
int a = 10;
String b = String.format("%d", 10);
```

## StringBuilder
```java linenos
StringBuilder string = new StringBuilder;
string.append("like").append(" this");
String a = string.toString();
```