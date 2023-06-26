---
tags: C++ 模板
aliase: 
created: 2023-02-04 21:20
modified: 星期六 4日 二月 2023 21:20:39
---

# C++ friend 與模板函式使用 LNK1120
***
## 內部類宣告有元函式未加template

```cpp
template <typename T>
class Base {
public:
	friend ostream& operator<<(ostream& out, Base<T>& b);// 錯誤
};

template<typename T>
ostream& operator<<(ostream& out, Base<T>& b) {
	out << "test";
	return out;
}
```

### 解決：
1. friend 前加模板
```cpp
template <typename U>
friend ostream& operator<<(ostream& out, Base<U>& b);// 增加模板U
```

2. 宣告與定義放在一起
```cpp
friend ostream& operator<<(ostream& out, Base<T>& b){
	out << "test";
	return out;
}
```

