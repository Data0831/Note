---
tags: C++ 錯誤處理
aliase: 
created: 2023-02-01 12:19
modified: 星期三 1日 二月 2023 12:19:26
---

# C++ 錯誤處理 exception handling
***
>[!info]+
>`try`: 放要執行的程式碼
>`throw`: 丟出錯誤，可以丟型態、物件 像`return`
>`catch`(): 接收錯誤並反映

- 若只用 throw 是沒有辦法提示信息的，只會有`abort called`介面

### try catch 與 throw
```cpp
try {throw "error";} // 放在try
catch (const char* msg) {cerr << msg;}
```
>發生錯誤並不會停下，若單純用throw則會停下
### exception
>[!info]+
>C++ 有很多種 exception 我們也可以去自訂義

自訂義：
```cpp
struct myException : exception {
	const char* what() const throw() {
		return "Error!!!";
	}
};
```
配合 `try` `catch`：
```cpp
try {
	throw myException();//myException() 初始化
}
catch (myException e) {
	cerr << e.what();
}
```
