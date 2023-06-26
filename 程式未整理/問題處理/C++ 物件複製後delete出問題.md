---
tags: C++ 物件複製 內存
aliase: 
created: 2023-02-03 12:51
modified: 星期五 3日 二月 2023 12:51:27
---

# C++ 物件複製後delete出問題
***
```cpp
// Base.h
class Base {
public:
	T* arr = new T[10];
	Base();
	~Base(){
		delete[] arr;
	}
};
```

```cpp
int main() {
	Base<int> a;
	Base<int> b = a;//報錯 CrtksValidHeapPointer(block)
}
```

兩個物件裡有不同地址的`arr`指標，但`arr`指標<mark style="background: #FFB86CA6;">申請到的記憶體空間相同</mark>，解構時delete對同一塊記憶體釋放兩次導致的錯誤

>釋放其中一個指標指向的內存空間時，另一個指標也會指向一塊已經被釋放的內存，造成了內存泄漏

### 解決：
1. 使用複製建構子


>[!question]+
為什麼編譯器讓兩個 `arr` 申請到同一塊記憶體

>[!sucess]+
編譯器是在確保程式運行時所需的資源與時間最佳化，為了達到這樣的目的，會對類別的附加的記憶體空間作一些最佳化的處理，所以這種情況會發生。

參考：[[C++ 複製#不安全的複製]]