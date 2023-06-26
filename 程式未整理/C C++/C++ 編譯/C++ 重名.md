---
tags: C++ 重名
aliase: 
created: 2023-02-02 12:46
modified: 星期四 2日 二月 2023 12:46:58
---

# C++ 重名
***

| 重名    | var | func | class |
|:------|:----|:-----|:------|
| var   | 可   | 否    | 可     |
| func  | 否   | 可    | 可     |
| class | 可   | 可    | 否     |  

var 、func
>變數不可與函式重名，因為有函式指標的問題

func 、func
>需要參數不同才可重名->overloading

>[!note]+
>也可以利用 namespace 解決重名問題

