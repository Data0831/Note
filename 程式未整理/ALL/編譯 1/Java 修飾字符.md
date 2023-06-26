---
tags: Java
aliase: modifier
created: 2023-01-12 08:07
modified: 星期四 12日 一月 2023 08:07:54
---

# Java 修飾字符
***
## static
![[Java 修飾字]]
### block

>[!info]+
>當物件被創建時執行static區域，最多執行一次
>-> 若沒有創建，便不會執行

```java
class A2{ 
	static{System.out.println("static block is invoked");} 
	public static void main(String args[]){ 
		System.out.println("Hello main"); 
	} 
}
```
第2句代碼將會被執行，而且比main先執行

## final
>[!info]+
>類似C++的[[程式未整理/C C++/C++ 編譯/C++ 修飾字#Constant|const]]
>使變數不能被修改
>讓子類不能定義父類的final方法

```java
public static final int ELEMENT_NOT_FOUND = -1;
```



