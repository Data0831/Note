---
tags: Python
aliase: string
created: 2022-12-23 23:08
modified: 星期四 12日 一月 2023 15:35:40
---
# Python 常用函式
***
# Python 數學

- math.atan2(num, num)
- math.cos(angle)
- math.sin(angle)

## sorted

`syntax: list = sorted(iterable, cmp=None, key=None, reverse=False)`

```python=
a = [0,3,7,8,9]
sorted(a, reverse=True)
```
sorted 可以对所有可迭代的对象进行排序操作
[詳細資料](https://www.runoob.com/python/python-func-sorted.html)

***
## randrange

**EXAMPLE**
```python
print(random.randrange(0,30))# output 0~29 one
```

## random choice
**EXAMPLE**
```python=
alist=["su3", "aivn", "plo"]
print(random.choice(alist))# iterable
```

## random.random
**EXAMPLE**
```python=
print(random.random())# return 0~1 float
```

***

# os
## path join
**EXAMPLE**
```python=
print(os.path.join("python", "space", "img"))# return str
```



