---
tags: Java 
aliase: 
created: 2023-02-22 13:05
modified: 星期三 22日 二月 2023 13:05:27
---

# Java Object型別
***
## 父類別object
>[!info]+
>所有java物件都有默認繼承類--> object
>可以透過轉型來new一個物件陣列

```java
E[] newElements = (E[]) new Object[newCapacity];
```
>當我們要用模板生成不同物件時可使用

## Object自帶方法
### toString

>[!info]+
>若有定義toString方法則回傳toString定義的字串，否則輸出物件本身地址


### finalize 遺言
```java
protected void finalize() throws Throwable{
	System.out.println("Person - finalize");
}
```

### equals

>[!info]+
>可自定義比較方法，若equals方法未定義，呼叫時默認比較地址
