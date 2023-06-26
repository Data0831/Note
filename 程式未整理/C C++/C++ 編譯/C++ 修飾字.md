---
tags: C++
aliase: modifier
created: 2023-01-04 18:00
modified: 星期五 6日 一月 2023 11:49:11
---

# C++ 修飾字
***

![[C++ 指標#const]]


## static
>[!info]+
>存取區域(scope)未改變，但生命週期持續到程式結束為止

static + var/func: 
```cpp
// local 
static int a = 10 //固定存取範圍(scope不改變、但被固定)，存活到程式死亡
// global
static int a = 10 
static int b(){ return 10 }; 
```
- static + global 與區域變數相同，通常用作防止其他檔案的extern使用
- static + func 與全域變數相同，通常用作防止其他檔案的extern使用

static + class member :
![[程式未整理/ALL/物件/C++ 修飾字#靜態成員 Static Memeber]]

## inline

inline + func :
```cpp 
inline int a(){ return 10 }; 
```
***
## extern

>[!info]+
>多個檔案共用變數使用
>extern 與 include 、static 不相容

```cpp 
//a.cpp
int x = 10;
int add(int n1, int n2){
	return n1 + n2;
}

//b.cpp
extern int x;//使用其他檔案的變數
extern int add(int n1, int n2);//使用其他檔案的函式
cout << x; //10
cout << add(x, 6); //16
```

- 不能使用在 static 變數，因為 static 限制了存取區域(scope)
- extern 、include 限制：[[C++ include extern 同時使用]]

***
## auto
>[!info]+
>編譯器根據變數的資料來判斷實際的型別

```cpp
auto a = 10;//編譯 -> int a = 10;
```
>若沒有給值編譯器將無法判斷型別 -> 報錯

在C++14中可以當作回傳值
```cpp
auto add(int a, int b){
	return a+b;
}
```

可參考：[auto](https://blog.gtwang.org/programming/cpp-auto-variable-tutorial/)




