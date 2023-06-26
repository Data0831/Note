---
tags: C++ 類別
aliase: C2143 內部類 
created: 2023-02-05 15:16
modified: 星期日 5日 二月 2023 15:16:24
---

# C++ 內部類在外部使用
***
當想在外部使用內部類時可能會遇到編譯器識別不了的問題
```cpp
template<typename T>
class out {
	static class inner {public:T val;};
	inner* first = nullptr;
	template<typename U>
	friend void print(out<U>& a);
};

template<typename T>
void print(out<T>& data){
	inner* d = data.first;// 報錯 無法讀取
}
```
此時編譯器表示找不到無法讀取，我們用out指定
```cpp
template<typename T>
void print(out<T>& data){
	out<T>::inner* d = data.first;// 報錯 無法讀取
}
```
還是一樣找不到
>[!info]+
>當使用內部類做型別時編譯器會偵測不到，需要在前方加typename編譯器才會將此視作型別

### 解決：

```cpp
template<typename T>
void print(out<T>& data){
	typename out<T>::inner* d = data.first;// 成功讀取
}
```

參考：[C2143](https://learn.microsoft.com/zh-tw/cpp/error-messages/compiler-errors-1/compiler-error-c2143?f1url=%3FappId%3DDev16IDEF1%26l%3DZH-TW%26k%3Dk(C2143)%26rd%3Dtrue&view=msvc-170)