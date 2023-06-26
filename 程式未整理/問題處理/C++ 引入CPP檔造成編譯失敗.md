---
tags: C++ 
aliase: 
created: 2023-02-18 16:24
modified: 星期六 18日 二月 2023 16:24:03
---

# C++ 引入CPP檔造成編譯失敗
***

```cpp
// main.cpp
#include<iostream>
#include"Calculator.cpp"

using namespace std;
int main() {
	return 0;
}


// Calculator.cpp
#pragma once
bool separate(char* Expression,char* Ans, char* Num) {
	return true;
}

以上程式在編譯時發生錯誤，LNK2005 LNK1169
```

- 引入CPP檔不安全，上述例子因為main引入了calculator造成calculato被重複編譯了兩次
- 若想將宣告與定義放在一起，可以都放入.h檔