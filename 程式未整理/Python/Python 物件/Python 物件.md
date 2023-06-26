---
tags: Python
aliase: class
created: 2022-12-27 15:29
modified: 星期四 5日 一月 2023 06:23:28
---
# Python 物件
***

## 定義類

>[!info]+
>C++ 中有兩種方法，給物件裡的資料賦值

```Python
class MyClass:# 定義變數時直接賦值
    x = 0
    ...
    def __init__(self):# 類別的建構子中賦值
        self.y = "default"
```

## 刪除物件
```python
del p1 # 使用del刪除物件
```

## 繼承
`class SubClass(SuperClass)`
```python=
class Shape:
    def __init__(self, x):
        self.x = x

class Circle(Shape):
    def __init__(self, x):
        super().__init__(x)

```
- 不一定要用self這個名字
- 要記得將繼承過來的class初始化

## 物件成員
### 建構子
```python
class Person:
    def __init__(self, name, age=18):
        self.name = name
        self.age = age

p = Person('Alice')
print(p.name)  # 輸出 'Alice'
print(p.age)  # 輸出 18
```

### 輸出
```python
class Person:
  def __str__(ugly):# __str__ 為規定輸出的函式
    return "hello"
    
p1 = Person()
print(p1)
```
