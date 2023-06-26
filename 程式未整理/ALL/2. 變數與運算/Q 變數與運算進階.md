---
tags: ALL
aliase: 
created: 2023-03-30 20:56
modified: 星期四 30日 三月 2023 20:56:12
---

# Q ++ 運算符
***

```cpp title:"C++第一題" 
int x = 5;
cout << x++ + ++x; 
```

```result 
12 (不該使用)
```

```Java title:"Java第一題" 
int x = 5;
System.out.println(x++ + ++x);
```

```result 
12 (不該使用)
```

---

```cpp title:"cpp第二題"
int x = 5;
cout << --++x; 
```

```result
5 (不該使用)
```

```Java title:"Java第二題" 
int x = 5;
System.out.println(--++x);
```

```result 
Error
```
---

```cpp title:"c++第三題"
int x = 5;
cout << ++++x++; 
```

```result
Error
```

```Java title:"Java第三題" 
int x = 5;
System.out.println(++++x++);
```

```result 
Error
```


---

```cpp title:"c++第四題"
int x = 5;
cout << x-- + ++x; 
```

```result
12 msvc (不該使用) 10 mingw
```

```Java title:"Java第四題" 
int x = 5;
System.out.println(x-- + ++x);
```

```result 
10 (不該使用)
```

---

```cpp title:"c++第五題"
int x = 5;
x++ = 86;
cout << x;
```

```result
Error
```

```Java title:"Java第五題" 
int x = 5;
x++ = 86;
System.out.println(x);
```

```result 
Error
```

---
```cpp title:"c++第六題"
int x = 5;
++x = 86;
cout << x;
```

```result
86
```

```Java title:"Java第六題" 
int x = 5;
++x = 86;
System.out.println(x);
```

```result 
Error
```

---
# Q 題目

1. 請問以下的變數創建有問題嗎？
```java linenos title:"Error"
float a = 10.1; 
```

>[!note]- Ans
>incorrect 
10.1-> 10.1f

2. 請問java與C(C++)的float、double各別使用哪種格式控制符？

>[!note]- Ans
Java: %f輸出float 與 double
C、C++: %f輸出float %lf 輸出double

3. Java 以下程式碼有錯嗎？

``` java linenos
int num = 1, res = 1;
num = (!res)? 10 : 20;
```

>[!note]- Ans
邏輯非不能對數字做運算(C與C++可以)

4. Java 以下程式碼有錯嗎？

```java linenos
public class Test {
	public static void main(String args[]) {
		static int x;
		System.out.println(x);
	}
}
```

>[!note]- Ans
method 裡的變數只能加上final，static是不合法的

5. C 以下程式碼的輸出？

```cpp linenos
int a, b = 55, c = 55.001;
a = b == c;
printf("%d", a);
```

>[!note]- Ans
1

6. 請問以下C程式碼能在Java中執行嗎？
```cpp
int a = 10.1;// a = 10
```

>[!note]- Ans
>不行，Java不支持**大轉小**的自動轉換，但可以小轉大 -> `double a = 10`
