---
tags: C++ 文件
aliase: 
created: 2023-02-01 19:42
modified: 星期三 1日 二月 2023 19:42:28
---

# C++ include extern 同時使用
***
>當cpp被include，就不能用extern去存取include的cpp變數
```cpp
//test.cpp
int a = 10;

//main.cpp
#include "test.cpp"
extern int a;// include 不能與 extern同時使用
cout << a;
```

>如果將 include 與 extern同時使用編譯器會報錯->多重宣告

參考：[[程式未整理/C C++/C++ 編譯/C++ 修飾字#extern]]