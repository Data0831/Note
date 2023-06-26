---
tags: Python 
aliase: 
created: 2023-02-22 17:34
modified: 星期三 22日 二月 2023 17:34:32
---

# Python lambda
***
lambda arguments : expression
```python
def myfunc(n):
  return lambda a : a * n
mydoubler = myfunc(2)
mytripler = myfunc(3)
print(mydoubler(11))
print(mytripler(11))
# lambda 用來隱藏函式 或用來創造多個function
```
