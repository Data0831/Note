---
tags: C++ 模板類的繼承
aliase: 
created: 2023-02-04 14:56
modified: 星期六 4日 二月 2023 14:56:34
---

# C++ 模板類的繼承
***

>[!info]+
>模板在繼承中可能會造成 `C3861` `C2065` 未宣告的識別項
>因為在繼承的時後<mark style="background: #FFB86CA6;">模板未實體化</mark>，定義時會有問題

```cpp
template <typename T>
class Base{
public:
	static const int a = 5;
	int b = 10;
}
template <typename T>
class Inher:Base<T>{
public:
	void out(){
		cout << this->a << Base<T>::b;// 用this
	}
}
```

>使用 this指標->變數 或 類名<T>::變數