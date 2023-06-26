---
tags: C++ 
aliase: 
created: 2023-02-02 20:00
modified: 星期四 2日 二月 2023 20:00:56
---

# C++ 複製
***

## 使用構造函數複製

```cpp
template<typename T>
class Base {
public:
    T* arr = new T[10];
    Base();
    Base(const Base& other);//構造複製函式
    ~Base();
};

template<typename T>
Base<T>::Base(const Base& other) {//複製
    arr = new T[10];
    std::copy(other.arr, other.arr + 10, arr);
}
```


***
## 不安全的複製
### 用等號複製、當作參數傳遞

>[!info]+
>1. 當對象進行傳遞、複製時，會創建一個<mark style="background: #FFB8EBA6;">全新且完全獨立</mark>的對象
>2. 複製的副本在解構後不會影響到原本的對象
>3. 兩對象內的成員內存地址不會相同

>如果這個副本在內存中所分配的空間，與原本對象所分配的空間是同一個地址，則釋放該內存空間就會影響到原本對象，這時就會發生內存洩漏等錯誤。
-> A new一個空間，與b new的空間地址重疊 
### 動態分配問題
>[!danger]+
>當類別內有動態分配的記憶體，此時做不安全的複製將導致內存洩漏

>使用構造函數複製就不回出問題了！

詳細資料：[[C++ 物件複製後delete出問題]]

***





