---
tags: Java 
aliase: 
created: 2023-04-15 22:20
modified: 星期六 15日 四月 2023 22:20:15
---

# Java 函式
***
# 函式性質
>[!info]+
>在函式中自動宣告的變數、陣列、物件將會在函式*生命週期結束後銷毀*。

- instance (實例): class內
	- class 實體化-> 透過物件呼叫
- static (靜態): static修飾字
	- class 定義後便存在，可以用類名(className)呼叫，也可以用物件(object)呼叫

```java linenos title:"範例" highlight:"7"
class Test {
	public static void instanceF(float a, float b) {}
	public static void staticF(double a, double b) {}
}
public class Main {
	public static void main(String args[]) {
		Test.instanceF();// 錯誤
		Test.staticF();//正常執行
		Test test = new Test();
		test.instanceF();//正常執行
		test.staticF();//正常執行
	}
}
```


---
# main 函式

>[!info]+
>程式執行開始的地方

```java title:"prog.java"
static void main(String args[]){}
```

```bash title:"console" prompt:"C:"
javac prog.java
java prog.java 5 4.4 test1.txt
```

- args:
    - args\[0]: "5"
    - args\[1]: "4.4"
    - args\[2]: "test.txt"

---
# 遞迴 recursive

>[!info]+
>遞迴應要制定*停止條件*

```java linenos title:"階層"
int factorial(int n) {
	if (n == 0) { return 1; }// 停止條件 
	else { return n * factorial(n - 1); } 
}
```

---
# 多型 overloading (polymorphisms)

>[!info]+
>函式名相同，*參數量*、*參數類型*、*順序不同*

```java title:"宣告"
add();
add(int a, int b);
```

**Q**:請問add(10, 10)呼叫哪個函式？ 
```java title:"宣告"
int add(double n1, double n2)
int add(float n1, float n2)
```
```result 
呼叫 add(float n1, float n2);
跟據widening 自動轉型， int -> float (先選較小的)
```

>[!info]
>調用函式時，*隱性轉換*(Widening)不會導致*二義性*
>調用add(10,10) 編譯器會根據widening的順序去調用

>[!warning]+
>java並沒有**默認參數**、**函式指標**、**運算元重載**

```java highlight:"1" title:"錯誤範例"
int add(double n1, double n2)//
```

---
