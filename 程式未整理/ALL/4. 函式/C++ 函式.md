---
tags: C++ 
aliase: 
created: 2023-04-15 14:37
modified: 星期六 15日 四月 2023 14:37:56
---

# C++ 函式
***
# 函式性質
>[!info]+
>在函式中自動宣告的變數、陣列、物件將會在函式*生命週期結束後銷毀*。

- 宣告 declear 根據情況可以*不加變數名字*，若要使用默認參數則須加上*參數名與默認值*
- 定義 definition 使用默認數時，只在宣告上寫上便可

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
# 多型 overloading (polymorphisms)

>[!info]+
>函式名相同，*參數量*、*參數類型*、*順序不同*

```cpp title:"宣告"
add();
add(int a, int b);
```

>[!note]+
>C++編譯器默認對符號名(函式名)作改編，此技術稱為*name mangling*或者叫*name decoration*， 不同編譯器改編方式可能會不同

**Q**:請問add(10, 10)呼叫哪個函式？ 
```cpp title:"宣告" highlight:"1-2"
int add(double n1, double n2=7);
int add(float n1, float n2);
```
```result 
編譯器錯誤
```

>[!warning]-
>調用函式時，*隱性轉換*(coercion)可能導致二義性
>當調用add(10,10) 編譯器會*無法分辨*該呼叫哪個函式

## 默認參數 default parameters

>[!info]+
>默認參數要從**最右邊**開始分配，只放在**宣告**裡

```cpp title:"宣告與定義"
int add();//宣告
int add(int a, int b=2);//宣告時放入默認參數，最右邊開始

int add(){return 0;}//定義
int add(int a, int b){return a+b;}//定義
```

**Q**: 請問 add function透過<u>參數量的變化</u>有多少種呼叫方法？

>[!note]- Ans
>3種: add()、add(int)、add(int, int)

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

## 函式名當參數 

>[!warning]+
>注意! 使用**func表示函式指標**，func()才是表示呼叫函式，也就是說可以把**函式名當參數傳遞** 

```cpp linenos title:"函式名當參數"
int add(int n1, int n2){// add function
	return n1 + n2;
}

void print(int (*fun)(int, int), int n1, int n2) {//print function
	cout << fun(n1, n2) << endl;
}

int main() {
	print(add, 10, 15); // 25
}
```

>[!success]+ Point
>使用函式指標時*默認參數*將失效

```cpp linenos
void test(int a, int b=3){}

int main(){
    void (*ptr)(int,int) = test;
    ptr(3);// 錯誤， 使用test(3)沒有問題，但使用ptr(3)會報錯
    return 0;
}
```
```result
編譯失敗
```
```result prompt:"解釋"
函式指標會忽略默認參數
```

## 函式指標與多型
>[!info]+
>函式指標並不能使用多型，除非使用class配合virtual

- **一般**:
```cpp linenos title:"兩種test"
void test(int a){}
void test(int a, int b=3){}
```

```cpp linenos 
void (*ptr)(int,int) = test;
test(1);//正常執行
test(1, 2);//正常執行
ptr(1);// 錯誤
ptr(1,2);// 正常執行
```

- **superclass + virtual**
```cpp linenos title:"superclass"
class Shape {
public: virtual void draw() = 0;//不能實作，需要宣告為抽象方法
};
```

```cpp linenos title:"subclass1"
class Circle : public Shape {
public: void draw() {cout << "Drawing a circle" << endl;}
};
```

```cpp linenos title:"subclass2"
class Square : public Shape {
public: void draw() {cout << "Drawing a square" << endl;}
};
```

```cpp linenos title:"main"
int main() {
    Shape* shapes[2];
    Circle c;Square s;
    shapes[0] = &c;shapes[1] = &s;

    void (Shape::*fp)() = &Shape::draw;
    for (int i = 0; i < 2; i++) {
        (shapes[i]->*fp)();//因為*fp 為抽象方法，所以呼叫時可以根據子類進行動態綁定
    }
}
```

>[!success]+ Point
>1. **superclass/base class** 陣列可以放入衍生類(derive class)
>2. **superclass** 必須為**抽象**類型，否則呼叫 `shapes[i]->*fp` 時將會變成呼叫Shape的draw方法

---

# 運算符重載 operator overloading

>[!info]+ 規則
>data1 運算符 data2 -> 參數1:data1 參數2:data2\
>`type operator(type &data1, type &data2);`
## cout << 重載

```cpp
class Base{
public:
	int a = 10;
};
ostream& operator<<(ostream& out, Base& b){
	out << b.a; //運算符左為參數一，右為參數二
	return out;
}
```
