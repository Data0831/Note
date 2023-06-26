---
tags: Python 轉型
aliase: 
created: 2023-02-22 14:31
modified: 星期三 22日 二月 2023 14:31:43
---

# Python 轉型
***
## float casting to int wiil floor num

```python=
# 使用 int 函數將浮點數轉換為整數
x = int(3.14)  # x 為 3
y = int(3.9)   # y 為 3
z = int(-3.14) # z 為 -3

# 使用數學運算符 // 將浮點數轉換為整數
x = 3.14 // 1  # x 為 3
y = 3.9  // 1  # y 為 3
z = -3.14 // 1 # z 為 -3
```
無條件捨去小數點