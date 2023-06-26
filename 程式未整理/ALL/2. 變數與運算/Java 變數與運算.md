---
tags: Java 變數
aliase: 
created: 2023-03-29 11:43
modified: 星期三 29日 三月 2023 11:43:47
---

# Java 變數與運算
***
# 變數型態 Data type
1. 整數: byte, short、int、long、long long
2. 浮點數: float、double、long double
3. 字元: char(2byte) `String並不是一個型態`
4. 布林: boolean

## 宣告與存取域 scope
>[!info]+
>1. 宣告變數時編譯器會生成一塊空間(內存)來存取變數，若變數未賦值(assign value)直接存取會造成**錯誤(checked exception)**
>2. 變數的存取範圍為*最近的大括號*，存活時間(life time)為大括號*對應的函式執行中止*為止

1. instance(實例): class內定義、不在method裡
	1. 若沒有賦值，實體化時會被JVM分配默認值
2. Static/class(靜態):加上static
	1. 若沒有賦值，實體化時會被JVM分配默認值
3. local(區域): 函式內
	1. 若沒有賦值，則禁止存取

```cpp linenos title:"範例"
public class Main {
	int n1 = 0;// instance variable
	Static n2 = 0;// static variable
	public static void main(String args[]) {
		int n2 = 0; // local variable
	// 最近的大括號-> 在main中使用，函式生命結束後，內存空間被回收
		int n3;
		System.out.println(n3);
	}
}

```
```result
編譯錯誤
```


## 轉型 type casting

```java linenos title:"轉型"
//1. Narrowing 強制轉型
boolean someBool = (boolean)someInt;
//2. Widening 隱性/自動轉型
boolean someInt = someDouble;
```

- Widening (自動轉型)：將較小的數據類型轉換為較大的數據類型，並且不需要顯式地指定轉換類型。
```java linenos title:"轉型優先順序"
byte -> short -> int -> long -> float -> double
char -> int -> long -> float -> double
```

>[!warning]+
>將float轉型成double是危險的，會丟失*精度*

## 默認常量
```java linenos title:"Error"
20; //int
10.1f; //float
10.1; //double
true;
's';
"asd";//String
```

## 進制

```java linenos
int decimalValue = 123; // decimal-form literal
int octalValue = 01200; // octal-form literal; add “0”
int hexaDecimalValue = 0xAce; // Hexa-decimal form literal; add “0x”
int binaryValue = 0b00101; // Binary literal; add “0b”
```

--- 
# 修飾字 modifier
## static
>[!info]+
>**static + 變數**: 存取域(scope)不改變，但存活時間變成至程式結束為止，通常用在類別
>特性: 只會生成一次

```cpp linenos title:"示例"
static int Value1 = 123; 
```
## final
>[!info]+
>**final + 變數**: 禁止修改值

---
# 運算子 operator
## 運算符優先順序
1. 遞增減運算符: ++, --
2. 單元運算子 (unary)
	- 正負號: +, -
	- 位運算comp: ~
3. 二元運算 (binary)
	1. 算數
		1. \* / % 
		2. \+ \-
	2. 位移: << >> >>>
	3. 關係: 
		1. < <= > >=, instanceof
		2. == !=
	4. 位運算
		1. and: &
		2. Xor:^
		3. or:|
	5. 邏輯
		1. &&
		2. ||
	6. 條件(ternary): ?:
	7. 賦值: = += -= \*= /= %= &= ^= |= <<= >>= >>>=

---


## ++ 運算符

>[!success]+ 定義
>**++x**: x+=1 後返回x的數值
>**x++**: 將x的數值返回，之後變數x+=1

```cpp linenos
int x = 5;
cout << x++ + ++x; // output 12
```

```cpp linenos
int x = 5;
cout << x-- + ++x; // 10
```

>從做至右
- **不要在一個運算式(expression)中對同個變數使用多個++、--運算子**: [[C++ 變數與運算#++ 運算符]]

>[!note]+
>在Java中，在表示式對同一個變量進行**前綴和後綴**自增或自減操作會導致未定義行為。++x++ 的運算順序是未定義的（undefined behavior）

```cpp linenos
int x = 5;
cout << ++x++; //error
```


