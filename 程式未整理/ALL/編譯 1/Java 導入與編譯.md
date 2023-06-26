---
tags: Java
aliase: system
created: 2023-01-02 01:25
modified: 星期四 12日 一月 2023 14:42:25
---

# Java 導入與編譯
***

# Java 系統相關
## main
```java=
package com.package_name;

public class Classname {
	public static void main(String[] args) {
	}
}
```
main 的格式不能去做更動，尤其是參數部分，不然Java無法執行


## 建議清除內存
```java=
System.gc()
```
>JVM在記憶體不夠時，會自動處理垃圾(未被引用的物件)，可使用上述方法建議JVM釋放記憶體

***

# Java 導入 多文件編譯

## interface
>[!info]+
>Java中接口裡只能存函式聲明，且所有聲明默認為public

```java
// List.java
public interface List<E>{
}
```

```java
public class ArrayList<E> implements List<E>{
}
```
> ArrayList 實現接口 List

有了街口我們可以做以下
```java
List<Integer> list1 = new ArrayList<>()
ArrayList<Integer> list1 = new ArrayList<>()
```
>兩句效果相同

## implements
>[!info]+
>implements用來實現接口
>詳細可以看

## abstract
>[!info]+
>抽象，用來修飾類，讓類不用完整的實現接口
>裡面可以放入抽象函式
>註：抽象函式不能實現，只有聲明。詳細請看

## extends
```java
public class ArrayList<E> extends List<E>{
}
```
> ArrayList 繼承 List

***