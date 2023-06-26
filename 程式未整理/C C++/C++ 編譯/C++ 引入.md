---
tags: C++ 重複引入
aliase: 
created: 2023-02-02 12:56
modified: 星期四 2日 二月 2023 12:56:03
---

# C++ 引入
***
## C++ 重複引入
>[!info]+
>為了避免重複引入我們會在程式碼最前面加入 `#ifndef` `#endif`

```cpp
#ifndef __MATH_H__
#define __MATH_H__

// program...

#endif
```

>[!info]+
>也可以使用 `#pragma once`

```cpp
#pragma once
//program ...
```

差別：
`#ifndef` 語言支持性較好，但define名稱相同就會出問題
`#pragma once` 保證文件只導入一次，但若有重複拷貝的文件也會被導入

## 引入 .h .cpp的差別

>[!info]+
>引入CPP檔是不安全的，有可能會造成編譯二次的問題，使用上面兩引用方法都是同樣的

- .h檔可以將宣告定義放在同個檔案，如同模板的寫法
- .cpp檔只能放定義

>編譯器連結編譯了兩次，造成LNK2005 LNK 1169
>詳情可以看 [[C++ 引入CPP檔造成編譯失敗]]