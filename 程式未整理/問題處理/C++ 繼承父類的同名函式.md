---
tags: C++ 重名 函式
aliase: 
created: 2023-02-04 12:14
modified: 星期六 4日 二月 2023 12:14:09
---

# C++ 與父類函式同名
***
>[!info]+
>父類函式與子類函式重名時，父類的函式將被隱藏起來

>只要同名，不論參數是否一致，父類成員函式都會被隱藏
```cpp
#include <iostream>
using namespace std;

class Base {
public:
    int add(int val) {
        return 20 + val;
    }
};

class Inher : public Base {
public:
    int add(int val1, int val2){
        return val1 + val2;
    }
};

int main() {
    Inher a;
    cout << a.add(3);//報錯 父類函式被隱藏
}
```

### 解決：

1. 子類定義是重載父類
```cpp
class Inher : public Base {
public:
	int add(int val){
		return Base::add(val); 
	}
    int add(int val1, int val2){
        return val1 + val2;
    }
};
```

2. 強制呼叫父類
```cpp
a.Base::add(3) 強制使用父類成員
```

詳細資料：[父类子类函数重载](https://gaocegege.com/Blog/cpp/cppkeng)

***