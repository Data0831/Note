---
tags: Q 指標進階
aliase: 
created: 2023-04-29 15:11
modified: 星期六 29日 四月 2023 15:11:13
---

# Q 指標進階
***
1. 請問以下C++程式碼有沒有錯？
```cpp
int& num_add(const int& num){
	return num;
}
```

>[!note]- Ans
>const ref 回傳也須加const

2. 請問以下C++程式碼有沒有錯？
```cpp
const int& func(int& num=3){
	return num;
}
```

>[!note]- Ans
>不能設定默認參數，詳細可參考[[ALL 函式]]

3. 請問以下C++程式碼有沒有錯？

```cpp
int a = 10;
const int* p = &a;
*p = 4;
```

>[!note]- Ans
>`const int* p`不能修改數字值，詳細可參考[[C++ 指標]]

4. 請問以下C++程式碼的輸出？
```cpp
int a[3] = { 0, 1, 2};
int* p = a;
cout << *p++;
```

>[!note]- Ans
>++優先級是最大的，所以`*p++` = `*(p++)` ，然後p++是先返回p在做p++，所以變成`cout << *(p)` 所以輸出為: 0

