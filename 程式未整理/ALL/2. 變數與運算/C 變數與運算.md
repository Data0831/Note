---
tags: C 
aliase: 
created: 2023-03-29 18:43
modified: 星期三 29日 三月 2023 18:43:48
---

# C 變數與運算
***
# 變數型態 Data type
1. 整數: short、int、long、long long
2. 浮點數: float、double、long double
3. 字元: char
4. 布林: bool

## 宣告與存取域 scope
>[!info]+
>1. 宣告變數時編譯器會生成一塊空間(內存)來存取變數，若變數未賦值(assign value)直接存取會存取到原本內存中的值，此動作稱作**undefine behavior(未定義行為)**
>2. 變數的存取範圍為*最近的大括號*，存活時間(life time)為大括號*對應的函式執行中止*為止

1. global(全域): main外定義
2. local(區域): 函式內

```cpp linenos title:"範例"
int x = 0; // global variable: 這份文件中都可存取

int main(){
	int n2 = 0; // local variable
	// 最近的大括號-> 在main中使用，函式生命結束後，內存空間被回收
	int n3;
	printg("%d", n3);
}
```
```result
4201120 // undefine behavior
```


## 轉型 type casting

```cpp linenos title:"轉型"
//1. common casting 強制轉型
bool someBool = (bool)someInt;
//2. natually
bool someBool = bool(someInt);
//3. verbose
bool someBool = static_cast<bool>(someInt);
//4. coercion 隱性轉型
bool someInt = someDouble;
```

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

```cpp linenos
int decimalValue = 123; // decimal-form literal
int octalValue = 01200; // octal-form literal; add “0”
int hexaDecimalValue = 0xAce; // Hexa-decimal form literal; add “0x”
int binaryValue = 0b00101; // Binary literal; add “0b”
```

---
# 修飾字 modifier
## static
>[!info]+
>**static + 變數**: 存取域(scope)不改變，但存活時間變成至程式結束為止，通常用在迴圈、類別
>特性: 只會生成一次

```cpp linenos title:"示例"
static int Value1 = 123; 

for (int i = 0; i < 5; i++) {
	static int Value2 = 13;// 只創建一次並且離開迴圈時仍存在
}
```
## const
>[!info]+
>**const + 變數**: 禁止修改值

---
# 運算子 operator

## 優先順序 precedence

>[!info]+
>**sizeof**不是函式而是運算子

0. sizeof()
1. 遞增減運算符: ++, --
2. 單元運算子 (unary)
	- 正負號: +, -
	- 邏輯非(可用在數字):  !
	- 位運算comp: ~
3. 二元運算 (binary)
	1. 算數
		1. \* / % 
		2. \+ \-
	2. 位移: << >>
	3. 關係: 
		1. < <= > >=
		2. == !=
	4. 位運算
		1. and: &
		2. Xor:^
		3. or:|
	5. 邏輯
		1. &&
		2. ||
	6. 條件(ternary): ?:
	7. 賦值: = += -= \*= /= %= &= ^= |= <<= >>=

---


## ++ 運算符

>[!success]+ 定義
>**++x**: x+=1 後返回變數x
>**x++**: 將x的數值返回，之後變數x+=1

```cpp linenos
int x = 5;
cout << x++ + ++x; // output 12
```

>[!warning]+
>在C中，每個compiler 對++x、x++ 順序有所不同，**不要在一個運算式(expression)中對同個變數使用多個++、--運算子**

```cpp linenos
int x = 5;
cout << x-- + ++x;
```

```result
12 (msvc)
10 (mingw)//不同編譯器計算的值不同
```

>[!note]+
>在C中，在表示式對同一個變量進行**前綴和後綴**自增或自減操作會導致未定義行為。++x++ 的運算順序是未定義的（undefined behavior）

```cpp linenos
int x = 5;
cout << ++x++; //error
```


---


