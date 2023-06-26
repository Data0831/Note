---
tags: Python 
aliase: 
created: 2023-02-22 14:32
modified: 星期三 22日 二月 2023 14:32:27
---

# Python 引用
***
# reference
## list append and variable ref
```python
def test_li():
    a = []
    num = 600
    for i in range(5):
        a.append(i)
    a.append(num)
    print(id(num))
    print(id(a[-1]))
    return a

b = test_li()
print(id(b[-1]))
```

append var是用var的ref
clear del 不會影響到var的存在
***