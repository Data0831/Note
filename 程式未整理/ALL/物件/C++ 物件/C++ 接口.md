---
tags: C++ 
aliase: 
created: 2023-02-04 16:06
modified: 星期六 4日 二月 2023 16:39:53
---

# C++ 接口
***

## 虛函式 virtual

>[!info]+
>虛函式算是一種為類別繼承所設計的類似接口的東西
### 虛函式特性
- virtual 修飾字只能放成員函式
>static 為類別共用無法覆寫，構造函式不能繼承
- virtual 修飾字只需放在宣告 
- 子類繼承父類的虛函式後，函式仍是 virtual 型態
>不是虛函式的成員函式，解析在編譯時而非運行時

Example：
```cpp
class Base{
	virtual void ex();//宣告
	virtual void ex2(){
	}//定義
};
void Base::ex(){};//定義 不加virtual
```
>繼承父類同名虛函式成員會隱藏，但既使 override 也可以透過父類名使用同名成員

### 純虛函式 pure virtual function
```cpp
virtual void ex3() = 0;// 只有宣告
```
- 純虛函式要求子類必須覆寫，虛函式並無此要求

可參考：[純虛函式](https://shengyu7697.github.io/cpp-virtual/)

## 覆寫 override
>[!info]+
>override 對虛函式進行覆寫

- 覆蓋的虛函式需要同名同型態
- override 修飾字只須放在宣告
- 純虛函數是必須覆寫的
>與隱藏相似，都是子類成員函式與父類重名 
>可參考：[[C++ 繼承父類的同名函式]]

Example:
```cpp
class Derived:Base{
	void ex() override;
	void ex2() override{
	}
}
void Base::ex(){}
```

可參考：[override 用法](https://blog.csdn.net/wfei101/article/details/82431644)

>[!question]+
>C++ virtual 函式繼承 與一般函式繼承差在哪裡，override會完全覆寫父類嗎？

A:與一般函式的繼承行為相同，雖然對父函式覆寫但仍然保留繼承下的同名成員

### 默認參數覆寫
>[!info]+
>override 可對默認參數覆寫

```cpp
virtual void fun1(int a = 10);
//a.cpp
void fun1(int a = 3) override;//改變參數
//b.cpp
void fun1(int a) override;//取消參數
```

***
## 禁止覆寫 final

>[!info]+
>禁止子類對虛函式做覆寫

Example:
```cpp
//class A
virtual void() {	} //定義虛函式
//class B:A
void() override final{	} // 禁止被覆蓋
//class C:B
void() override{	}//錯誤 繼承的B 有final修飾
```

參考：[虛函式](https://cloud.tencent.com/developer/article/1784495)  

***