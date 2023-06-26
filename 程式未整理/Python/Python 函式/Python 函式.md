---
tags: Python 
aliase: 
created: 2023-02-22 17:33
modified: 星期三 22日 二月 2023 17:33:09
---

# Python 函式
***

## 多重參數
function arguments:
```python
def my_function(*kids):
  print("The youngest child is " + kids[2])
my_function("Emil", "Tobias", "Linus")
# *代表tuple 意指傳入的參數全部被看做一個tuple

def my_function(**kid):
  print("His last name is " + kid["lname"])
my_function(fname = "Tobias", lname = "Refsnes")
# **像是dict 意指傳入的參數全部被看做一個dict
```
