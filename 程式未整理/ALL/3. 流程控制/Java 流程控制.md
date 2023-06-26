---
tags: Java 流程控制
aliase: 
created: 2023-03-29 18:58
modified: 星期三 29日 三月 2023 18:58:54
---

# Java 流程控制 flow control
***

# condition

>[!info]+
>Java 條件不能用數字必須是*布林值*

```java linenos title:"Error"
if(-1)//錯誤
	//do some thing
```

---

## ternary operator

```c linenos
int k = (a>b)? 13: 15; // if (a>b) k = 13 else k = 15
```

- if ... else
- switch


# loop

```cpp linenos title:"正常迴圈"
for(int i = 0;i < 10;i++)
```

```cpp linenos title:"list迴圈"
int a[5] = {1,2,3,4,5};
for(int i : a)
```

- for
- while
- do ... while