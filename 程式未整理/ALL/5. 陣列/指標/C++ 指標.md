---
tags: C++
aliase: reference
created: 2023-01-13 16:37
modified: 星期五 13日 一月 2023 16:37:08
---

# C++ 指標
***
>[!info]+
>指標常用來當作*參數傳遞*或是*動態配置記憶體*

## 1. void
```cpp linenos title:"void pointer"
int a = 10;
void* p = &a;
cout << *((int*)p); // 萬用指標使用時要轉型
```

## 2. function
```cpp linenos title:"function pointer"
int add(int n1, int n2){// add function
	return n1 + n2;
}

int sub(int n1, int n2){//sub function
	return n1 - n2;
}

void print(int (*fun)(int, int), int n1, int n2) {//print function
	cout << fun(n1, n2) << endl;
}

int main() {
	print(add, 10, 15);// 把函式名當參數傳遞時，會默認把函式當作指標傳遞
	print(sub, 100, 87);
	int (*add0)(int n1, int n2) = add;// 只呼叫函式名不加括號則默認把函式當作指標
	print(add0, 11, 13);
}
```
```result
25
13
24
```

>[!info]+
>只呼叫函式名**不加括號**則默認把函式當作指標

## 定義空指標
>[!info]+
>NULL nullptr 定義載 i/o 檔裡

```cpp
#ifndef NULL
#ifdef __cplusplus
#define NULL    0
#else  /* __cplusplus */
#define NULL    ((void *)0)
#endif  /* __cplusplus */
#endif  /* NULL */
```

可參考：[NULL](https://bbs.csdn.net/topics/390602299)

---
# C++ reference 
>[!info]+
>引用常用來當作*參數傳遞*，引用不能賦值

```cpp linenos title:"參數"
void func(int &a){}

int main(){
	int k = 0;
	func(k);
}
```


***

# const 修飾

>[!info]+
>const 修飾<mark style="background: #FF5582A6;">右邊的全部</mark>

const + ptr :
```cpp 
const int* p; // 修飾 *p -> 不能修改數字值
int* const p; // 修飾 p -> 不能修改地址
const int* const p; // 不能修改值、不能修改地址
```
const + ref :
```cpp 
const int& p1; // 修飾 &p -> 不能修改值
int& const p2; 
```

- constant reference : <mark style="background: #FFB86CA6;">const int& r</mark>
- pointer to a constant : <mark style="background: #FFB86CA6;">const int* p</mark>
- constant pointer : <mark style="background: #FFB86CA6;">int* const p</mark>
- constant pointer to a constant : <mark style="background: #FFB86CA6;">const int* const p</mark>