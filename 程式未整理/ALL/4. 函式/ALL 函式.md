---
tags: ALL 
aliase: 
created: 2023-04-29 15:12
modified: 星期六 29日 四月 2023 15:12:44
---

# ALL 函式
***

# 關於傳遞參數

```cpp linenos title:"正常"
int add(int n1, int n2){
	return n1+n2;
}
add(10,3);
```
可看成以下
```cpp linenos title:"編譯器幫你做的事"
int add(){// 編譯器幫你做的事
	int n1 = 10;// 宣告一個名為n1的變數並儲存傳過來的值
	int n2 = 3;
	return n1+n2;
}
```

上兩段程式碼作用是相同的，透過這種方法我們可以簡單的判斷合不合法

```cpp linenos title:"不合法"
void func(int& num=3){
}
func();
```

```cpp linenos title:"編譯器幫你做的事"
void func(){
	int& num=3; // 因為不能等於常量，所以不合法 
}
```

同樣的回傳型態也能用類似方法

---