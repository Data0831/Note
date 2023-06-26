---
tags: C++ string 函式
aliase: 
created: 2023-02-21 17:59
modified: 星期二 21日 二月 2023 17:59:41
---

# C++ string 物件方法
***
https://www.scaler.com/topics/cpp/strings-in-cpp/

string member function:

1. info
	- 長度
		- length() -> int
		- size() -> int
		- capacity() -> int 
		- max_size() -> int
	- 頭尾
		- begin() -> char&
		- back() -> char& 
		- cbegin() -> const_iterator 
		- cend() -> const_iterator 
		- crbegin() -> const_reverse_iterator 
		- front() -> char& 
		- rbegin() -> reverse_iterator 
		- end() -> iterator 
		- rend() -> reverse_iterator 
		- crend() -> const_reverse_iterator
	- empty() -> bool 
	- c_str() -> char* 
	- get_allocator() -> allocator_type 

2. 修改
	- 增 
		- insert() -> string& 
		- string& append(const string& str1) -> string&
		- 
		- data() -> const_char*
		- push_back(char c) -> void
		- copy(string& str1) -> int
	- 減
		- substr(int position, int len) -> string
		- erase() -> string& 
		- pop_back() -> void
		- clear() -> void
		- 
	- 改
		- void swap(string& str)
		- assign() -> string&
		- reserve(int length) -> void 
		- string& replace(int pos, int n, string& str1) -> string&
	- 長度修改
		- resize(int len) -> void
		- shrink_to_fit() -> void 

3. 比較
	- compare(string& str) -> int

4. 尋找
	- at(int position) -> char&
	- find_first_of(string& str1, int pos, int len) -> int
	- find_first_not_of(string& str1, int pos, int len) -> int
	- find_last_of(string& str1, int position, int n) -> int 
	- find_last_not_of(string& str1, int position) -> int 
	- rfind() -> int 







c++ 如何讓int變string

1.  使用 C 庫函數 `sprintf`：
```cpp
#include <cstdio>
#include <iostream>

int main() {
    int number = 42;
    char buffer[20];
    sprintf(buffer, "%d", number);
    std::string str(buffer);
    std::cout << str << std::endl;
    return 0;
}
```

2.  使用 C++ STL 中的 `stringstream`：

```cpp linos
#include <sstream>
#include <iostream>

int main() {
    int number = 42;
    std::stringstream ss;
    ss << number;
    std::string str = ss.str();
    std::cout << str << std::endl;
    return 0;
}

```


3.  使用 C++11 新增的 `to_string` 函數：

```cpp
#include <string>
#include <iostream>

int main() {
    int number = 42;
    std::string str = std::to_string(number);
    std::cout << str << std::endl;
    return 0;
}
```
