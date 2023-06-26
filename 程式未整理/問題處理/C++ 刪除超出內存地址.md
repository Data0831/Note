---
tags: C++ 內存
aliase: 
created: 2023-02-01 19:30
modified: 星期三 1日 二月 2023 19:30:42
---

# C++ 刪除超出內存地址
***
## 字串陣列缺少'\\0'導致delete刪除超過

```cpp
char tmp[20]="abcde";
//copy
char *text = new char[strlen(tmp)];
strcpy(text, tmp);// 複製時的尾部'\0'未複製到
delete[] text; // 刪除時沒有'\0'做限制，一直刪除字元，刪到了其他內存
```

在第6行時出現報錯
>crt detected that the application wrote to memory after end of heap buffer

### 解決
1. 長度加1
```cpp
char *text = new char[strlen(tmp)+1];
```


參考：[調試錯誤](https://www.twblogs.net/a/5b85992a2b71775d1cd34886)
***