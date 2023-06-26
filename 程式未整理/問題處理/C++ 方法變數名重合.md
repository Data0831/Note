---
tags: C++ 重名
aliase: 
created: 2023-02-01 19:31
modified: 星期三 1日 二月 2023 19:31:34
---

# C++ 方法與變數同名
***
```cpp
class Array{
int size = 0;
public:
	int size(){//報錯，不能重名
		return size;
	}
}
```

>[!info]+
>方法名與變數名在C++內不能相同，Java裡是可以的
### 解決：
1. 更改方法名


詳細請參考：[[C++ 重名]]