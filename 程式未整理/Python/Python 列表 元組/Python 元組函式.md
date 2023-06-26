---
tags: Python 
aliase: 
created: 2023-02-21 11:42
modified: 星期二 21日 二月 2023 11:42:17
---

# Python 元組函式
***
- index
- count

```python
thistuple = (1, 3, 7, 8, 7, 5, 4, 6, 8, 5)
x, y = thistuple.index(1), thistuple.count(5)
print(x, y)
# index 未找到 -> except
```