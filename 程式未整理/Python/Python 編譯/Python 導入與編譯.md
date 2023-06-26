---
tags: Python
aliase: system
created: 2023-01-02 20:30
modified: 星期四 12日 一月 2023 15:12:40
---

# Python 導入與編譯
***
## Python 全局變數

```python=
x = 1

def foo():
    global x
    x += 1

foo()
print(x)  # 輸出 2
```

***

# Python multi import

## 當import公用檔案時資料回同步更新
```python=
import data as d
import test1 as t
d.var += 15 #將d資料變更
print(d.var)#輸出d
t.prin_var()#其他檔案輸出d
```
由4,5行得知，當資料公用時修改，另一資料也能收到修改後的資料