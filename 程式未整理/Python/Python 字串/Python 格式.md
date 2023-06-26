---
tags: Python 
aliase: 
created: 2023-02-21 10:43
modified: 星期二 21日 二月 2023 10:43:34
---

# Python 格式
***
>[!info]+
>format 將字串透過大括號進行格式修改

- string.format(value1, value2...) -> string
```python
a = 10
w, x, y, z = f"1.{a}llk", "2.{price:.2f}llk",  "3.{:f}llk", "4.{0}llk"
print(w)  # fstring 必須放入已賦值的變數
print(x.format(price=49))  # 必須放入key=varible, key需符和字串裡的變數名，variable隨便給值
print(y.format(67))  # 67.0
print(z.format("52"))  # 索引與傳入參數的順序有對應關係
# 參數必須>=大括號的數量，都是將其他型態轉型成str
```

- {:}分號之後為格式
- {:<1}{:>8}{:^8} 與ljust, rjust, center相同
- {:=8} sign 與數字以空格隔開，總長>=8
- {: }{:+}{:-} 正正負 數前添加(space, +, -)號
- {:,}{:`_`} 大數每3位以,`_`隔開 1,000
- {:b}{:d}{:o}{:x}{:X} 轉成2,10,8,16位數
- {:e}{:e}科學記號表示
- {:f}{:F}浮點數
- {:%}百分比