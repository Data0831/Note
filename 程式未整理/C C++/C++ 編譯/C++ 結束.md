---
tags: C++ 結束
aliase: 
created: 2023-01-14 10:22
modified: 星期六 14日 一月 2023 10:22:02
---

# C++ 結束
***


EOF 文件結束符（End-Of-File）

>[!info]+
>- 表示文件\輸入流的末尾
>- fgetc 或 getchar 、 scanf 將在遇到 EOF 時返回負數
>- `Ctrl+C` 鍵並不會導致函數返回 EOF。相反，按下 `Ctrl+C` 鍵會導致程序發出中斷信號（SIGINT），並終止程序的執行
>- Ctrl+D 鍵（在 Unix 系統中） Ctrl+Z 鍵（在 Windows 系統中）代表 EOF

>visual studio ctrl+z要按==3==次才有效，可能為[bug](https://blog.csdn.net/qq_49496715/article/details/116745751)
***

## exit 函式
>[!info]+
>`exit(int)`

```cpp
if (argc != 2) { 
	fprintf(stderr, "Usage: %s filename\n", argv[0]); 
	exit(1); 
}
```

>[!note]+
>- 傳入0代表正常退出，非0為發生錯誤
>- 發生錯誤時用來強制退出

***
