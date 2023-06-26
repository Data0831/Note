---
tags: Java 
aliase: 
created: 2023-03-29 13:28
modified: 星期三 29日 三月 2023 13:28:37
---

# Java 輸出入IO
***
## print
- System.out.print(String)
- System.out.println(String)
- System.out.printf(String, other)
![[C 輸出入IO#格式控制符 I 格式 (format specifier)]]
![[C 輸出入IO#格式控制符 II 標示]]
### 格式控制符 III 長度與精度

- %1d: 字串默認靠為右，其餘補空
- %-2d: 字串靠左，其餘補空
- %.3f: 限制小數點長度
- %6.9s: 字串靠右，其餘補空，限制字串長度為0

---
## Java Scanner()

```Java
Scanner scanner = new Scanner(System.in)
```

- scanner.nextInt();
- scanner.nextFloat();
- scanner.nextChar();
- scanner.next(); 讀取一字串遇到'\\n'或*空白字元*則停止，不讀入'\n'，一定會讀到**非空白字元**才停止
- scanner.nextLine(); 讀取一字串遇到'\\n'則停止，並且將'\\n也讀入'，但不放入字串內
- scanner.close(); 關閉輸入檔案
