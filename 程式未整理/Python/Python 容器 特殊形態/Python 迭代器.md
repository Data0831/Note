---
tags: Python 
aliase: 
created: 2023-02-22 17:40
modified: 星期三 22日 二月 2023 17:40:42
---

# Python 迭代器
***

### tuple iterator
iterator: iter() and next()
```python
mytuple = ("apple", "banana", "cherry")
myit = iter(mytuple)
print(next(myit))
print(next(myit))
print(next(myit))
```

### class iterator

```python
class MyNumbers:
    def __iter__(self):
        self.num = 1
        return self
    def __next__(self):
        if self.num < 20:
            x = self.num
            self.num+=1
            return x
        else:
            raise StopIteration       
myclass = MyNumbers()
for i in myclass:
    print(i)
```

