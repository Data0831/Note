---
tags: C++ 傳入參數
aliase: 
created: 2023-02-02 19:23
modified: 星期四 2日 二月 2023 19:23:05
---

# C++ 傳入參數
***
var 、ptr 、class
```cpp
int func(int a);//傳入副本
int func(int* p);//傳入副本，可通過解參考修改內容值，但p本身存的地址值無法改變
int func(Class a);//傳入副本
```
ref
```cpp
int func(int& a);//傳入別名，與指標解參考類似
```
