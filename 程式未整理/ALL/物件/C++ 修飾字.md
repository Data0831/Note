---
tags: C++ 
aliase: 
created: 2023-02-01 21:05
modified: 星期三 1日 二月 2023 21:05:14
---

# C++ 修飾字
***
## 靜態成員 Static Memeber
>[!info]+
>1. 靜態成員在類別裡是<u>唯一</u>且<u>共用</u>的
>2. 靜態成員會自動初始化

### static
1. static + member
```cpp
class Base{
	static int num;
	static const int num = 10;// 常量可以直接定義
	static print(){
		cout << "Hello";
	}//使用 Base::print()呼叫
}
int Base::num = 10;//普通變數，需外部初始化
```

***
## 訪問修飾符/存取權限/繼承方法
### private
- 存取: 只有內部類，子類無法存取父類的private成員
- 繼承: 子類可存取父類的[保護、公共]資料，並將資料設為私有
### protected
- 存取:只有類別與子類別可以使用，外部不可使用
- 繼承:子類可存取父類的[保護、公共]資料，並將資料設為保護
### public
- 存取:都可以使用
- 繼承:子類可存取父類的[保護、公共]資料，並將保護資料設為保護，公共資料設為公共

>[!col]+
>|     | <mark style="background: #FFB8EBA6;">private</mark> | <mark style="background: #FFB8EBA6;">protected</mark> | <mark style="background: #FFB8EBA6;">public</mark> |
>|:----|:--------|:----------|:-------|
>| 內部  | 可&nbsp; | 可         | 可      |
>| 子類 | 否       | 可         | 可      |
>| 外部  | 否       | 否         | 可      |  
>>[!col]+
>| 父類   | 私有成員 | 保護成員 | 公有成員 |
>|:-----|:-----|:-----|:-----|
>| 私有繼承 | 否    | 否    | 否    |
>| 保護繼承 | 私有   | 保護   | 保護   |
>| 公共繼承 | 私有   | 保護   | 公有   |  
- 父類的私有子類也會繼承，但無法存取
- 可 、否->存取 
可參考：[C++ 繼承方法](https://crmne0707.pixnet.net/blog/post/317782896-c%2B%2B-%E9%A1%9E%E5%88%A5-class-%E7%B9%BC%E6%89%BF)
***

### friend
>[!info]+
>friend 能存取class的private成員

- friend 類<u>不能被繼承</u>
- friend 宣告<u>默認為public 、extern</u>
> friend 定義與宣告沒有要強制同文件

```cpp
class Base {
	friend void func(Base& x); //func 可存取 Base的私有
	friend class Base2;// Base2 可存取 Base的私有
};
```
可參考：[友元](https://blog.csdn.net/weixin_38293850/article/details/80191242)
***
## 防止修改 CONST
### const 物件
```cpp
Base <int> a;
const Base<int> b(a);
```

物件使用 const 編譯器將會限制無法修改值
- 不能用 "." 、"=" 修改內容值
- 只能存取公共變數 或 const公共成員函式
>const 物件 只會在外部產生，所以只能使用公共成員
### const 成員函式
>[!info]+
>當const 物件需要使用成員函式時會用到

使用 const後綴 時編譯器會限制函式無法修改值
- const 函式修改不了內容值
- const 成員函式 只能呼叫 const 成員函式

***



