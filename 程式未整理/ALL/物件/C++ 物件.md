---
tags: C++
aliase: 
created: 2023-01-06 13:09
modified: 星期六 28日 一月 2023 05:42:03
---

# C++ 創建 繼承
***
# 創建與初始化
## 定義與初始化
```cpp linenos title:"3種初始化方式"
class MyClass {
    int num = 0;// 1. 內部定義賦值
    int array[5], *arr;
    string str;
    char symbol;
    MyClass() : array{1,2,3,4,5}, str("hello"), arr(new int[4]{1,2,3,4}) {// 2. 構造函式賦值 
	    symbol = 'c';// 3. 構造函式賦值 
    }
}
```

### 宣告與定義分開
>[!info]+
>在C++中使用`::`界定符號來告訴compiler使用哪裡的東西

## 創建物件
```cpp linenos title:"3種創建方式"
MyClass c1 = MyClass();
MyClass *c2 = new MyClass();
MyClass *c3 = new MyClass;
MyClass c4[5]; //陣列創建法
```

## 建構子與解構子
>[!info]+
>constructor: 與class name同名，可直接呼叫或透過new運算子呼叫
>destructor: `~` + class name，class *生命週期結束*時自動呼叫

## this
>[!info]+
>`this`是一種指標，有兩種作用 1. 代表物件，2. 區分

```cpp linenos title:"this的作用"
void method(int num){// 方法
	cout << this.num;//區分num
}

Base* re_obj1(){ //透過this 回傳object
	return this;// return Base
}

Base* re_obj2(){ //透過new 回傳object
	return new Base();
}
```

***
# 繼承

>[!info]+
>Inheritance: 在 C++ 中，可以使用關鍵字 ` : ` 來實現繼承。
>子類繼承會獲得所有父類資料

## 繼承與建構子
>[!info]+
>子類不繼承父類的建構子，但會繼承父類建構子裡的定義並合併至子類的建構子，換句話說在呼叫子類的建構子前**會先呼叫父類的建構子**做初始化動作

```cpp linenos title:"繼承與建構子"
class Base {
public:
    int a = 3, b;
    Base() :b(10) {// 父類建構子與初始化
        cout << "Base 被呼叫" << endl;
    }
};

class Derive:Base {
public:
    Derive() {// 子類建構子會先呼叫父類建構子做初始化
        cout << "Derive 被呼叫 " << "從Base繼承了(a,b) = " << a << ' ' << b << endl;
    }
};

int main() {
    Derive a = Derive();
	return 0;
}
```
```result
Base 被呼叫
Derive 被呼叫 從Base繼承了(a,b) = 3 10
```

### 子類主動呼叫父類建構子
>[!info]+
>`:Base()`: 當父類有要求參數時，子類需要**主動傳遞參數**

```cpp linenos title:"子類傳參給父類建構子"
class Base {
public:
    int a;
    Base(int a) {this->a = a;}// 要求一參數 int
};

class Derive : public Base { 
public:
    Derive(int num) : Base(num) {//傳送num 
    }
};

int main() {
    Derive a = Derive(10);
    return 0;
}
```

## 重載 Override
>[!info]+
>子類與父類方法重名並且子類繼承於父類，此時同名方法會造成重載

```cpp linenos title:"子類傳參給父類建構子"
#include <iostream>
using namespace std;

class Base {
public:
    void out() { cout << "Base\n";}
};

class Derive : public Base { 
public:
    void out() { cout << "Derive\n";}// override
};

int main() {
    Derive a = Derive();
    a.out();
    return 0;
}
```
```result
Derive
```

>[!info]+
>重載方法不代表父類方法消失，可以透過`.Base::method()`來呼叫父類方法

```cpp linenos title:"透過指定class"
//main()
a.Base::out();
```

```cpp linenos title:"在子類中透過指定class"
class Derive : public Base { 
public:
    void out() { 
	    Base::method()
    }// override
};
```


### 子類 、父類 函式重名
>[!info]+
>子類 、父類 成員函式重名，父類函式將被隱藏起來

>編譯器特性：只要函式名重疊，不論參數都會被隱藏

詳細參考：[[C++ 繼承父類的同名函式]]

### 模板繼承
>[!info]+
>模板是在執行時才初始化，此時子類若想使用父類成員需要用以下兩種方法
>1. 使用this + 成員
>2. 使用父類名 + 模板`<T>` + 界定符號 `::` + 成員

詳細可參考：[[C++ 模板類的繼承]] [[C++ 物件]]

***