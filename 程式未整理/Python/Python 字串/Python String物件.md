---
tags: Python 
aliase: 
created: 2023-02-22 13:25
modified: 星期三 22日 二月 2023 13:25:54
---

# Python String物件
***

- 容器與字串分割
	- string.join(iterable) -> string
	- string.split(separator, (optional)maxsplit) -> list
	- string.rsplit(separator, (optional)maxsplit) -> list
	- string.partition() -> tuple
	- string.rpartition() -> tuple
	- string.splitlines(keeplinebreaks) -> list
- 擴大補字元
	- string.center(length, character) -> string
	- string.ljust(length, character) -> string
	- string.rjust(length, character) -> string
	- string.zfill(len) -> string
- 尋找字串
	- string.count(value, start, end) -> int or 0
	- string.find(value, start, end) -> int or -1
	- string.rfind(value, start, end) -> int or -1
	- string.index(value, start, end) -> int or exception
	- string.rindex(value, start, end) -> int or exception
- 頭尾確認
	- string.startswith(value, start, end) -> bool
	- string.endswith(value, start, end) -> bool
- 移除左右
	- string.lstrip(characters) -> string 
	- string.rstrip(characters) -> string 
	- string.strip(characters) -> string
- is系列 -> bool
	- isalnum()
	- isalpha()
	- islower()
	- isupper()
	- isspace()字串是不是由空白組合
	- istitle()字串裡每個單詞是不是首字大寫，其他小寫
	- isprintable() 字串裡有沒有跳脫字元(每個元素是不是都能印出)
	- isidentifier() 字串是不是符合命名規則
	- isdecimal() 一般整數，次方項不行，分數不行
	- isdigit()   一般整數，次方項可以，分數不行
	- isnumeric() 一般整數，次方項可以，分數可以- 
-  字串翻譯，替換
	- string.replace(oldvalue, newvalue, count)
	- string.maketrans(x, y, z) (字符,轉換字符,丟棄字符) -> 
	- string.translate(table)
- 不常用
	- string.encode(encoding=encoding, errors=errors)
	- string.expandtabs(tabsize)