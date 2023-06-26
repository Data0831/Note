---
tags: C 
aliase: 
created: 2023-04-16 08:10
modified: 星期日 16日 四月 2023 08:10:31
---

# C 函式
***
# 函式性質
>[!info]+
>在函式中自動宣告的變數、陣列、物件將會在函式*生命週期結束後銷毀*。

- 宣告 declear 根據情況可以*不加變數名字*
- 定義 definition

```cpp linenos title:"範例"
int add(int , int );// declear 不加變數名

int main() {}

int add(int a, int b){//definition
    return a+b; // implement 實做
}
```


---
# main 函式

>[!info]+
>程式執行開始的地方

```cpp title:"prog.cpp"
int main(int argc, char ** argv){}
```

```bash title:"console" prompt:"C:"
./prog.exe 5 4.4 test1.txt
```

- argc: 4(參數量)
- argv:
    - argv\[0]: "prog" (程式名)
    - argv\[1]: "5"
    - argv\[2]: "4.4"
    - argv\[3]: "test.txt"

---
# 遞迴 recursive

>[!info]+
>遞迴應要制定*停止條件*

```cpp linenos title:"階層"
int factorial(int n) {
	if (n == 0) { return 1; }// 停止條件 
	else { return n * factorial(n - 1); } 
}
```

---
# 函式指標 function pointer

>[!info]+
>函式指標使用 <mark style="background: #FFB86CA6;">(\*funcName)</mark> 表示，並且*參數種類*要與指定的函式相同

```cpp linenos title:"宣告與使用"
void func(int a){};
int main(){
    void (*ptr)(int) = func;// 宣告1
    void (*ptr)(int) = &func;// 宣告2
    ptr = func;
    ptr = &func;

	ptr(3);//使用 1
	(*ptr)(3);// 使用 2
}
```

在這個程式中，`ptr` 是一個指向函式的指標，即它存儲的是 `func` 函式的地址。`*ptr` 的結果是 `test` 函式本身，所以 `*ptr(3)` 的結果相當於調用 `func(3)` 函式。

簡單來說，`ptr` 存儲的是函式的地址，而 `*ptr` 則代表著函式本身。在這個程式中，`ptr` 和 `*ptr` 的作用是一樣的，只是用法不同。

>[!warning]+
>c並沒有**默認參數**、**函式指標**、**運算元重載**

---
