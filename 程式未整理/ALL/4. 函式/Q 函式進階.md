---
tags: ALL
aliase: 
created: 2023-04-15 20:44
modified: 星期六 15日 四月 2023 20:44:09
---

# Q 函式進階
***
1. 請問以下C++程式碼是否正確？

```cpp linenos 
void (*ptr)(int a=3,int b=4) = &test;
```

>[!note]- Ans
>函式指標只能指向函式本身，而不是函式的參數，因此無法給函式參數設置默認值。

2. 請問以下C++程式碼是否正確？
```cpp linenos 
add(int a=2, int b);//最右邊開始
```

>[!note]- Ans
>默認參數應從最右邊開始指派

3. 請問以下C++程式碼在第5行出錯，為什麼？
```cpp linenos
void test(int a, int b=3){
    cout << "2";
}
int main(){
    void (*ptr)(double, int) = test;// compilation error
}
```

>[!note]- Ans
>函式指標參數與指定函式的參數類型不一致

4. 請問以下C++程式碼是否正確？
```cpp linenos 
void (*ptr)(int a,int b) = &test(int a,int b);
```

>[!note]- Ans
>test不需要加參數

5. 請問以下C++程式碼是否正確？
```cpp title:"宣告與定義"
int add();
int add(int a, int b=2);

int add(){return 0;}
int add(int a, int b=2){return a+b;}
```

>[!note]- Ans
>第5行程式碼，宣告-定義分開式結構，(define)不能使用默認參數


