---
tags: Python
aliase: comprehension
created: 2022-12-31 02:32
modified: 星期四 12日 一月 2023 15:36:34
---
# Python 簡寫
***

### if else
```python
a = 2; b = 330
print("A") if a > b else print("=") if a == b else print("B")
```

```python
 return False if (len(s) == 0 or len(output) > 140) else output
```


### for list
`syntax: [return for i in iterable]`
```python
[i for i in range(5)]
# [0, 1, 2, 3, 4]
```
`syntax: [(true)return if condition else (false)return for i in iterable]`
```python
s = "amdioamASD"
[' ' + c if c.isupper() else c for c in s]
```

### dict
```python
string = "helloworld"
def count(string):
    return {i: string.count(i) for i in set(string)}
```
-> 將string轉為set就不會重複讀入字母

### 連續比較
```python
x = 10; y = 20; z = 30
if x < y < z: print('x is smaller than y and z')

items = [1, 2, 3, 4, 5]
for i in items: print(i)
```