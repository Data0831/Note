---
tags: Python 
aliase: 
created: 2023-02-22 14:09
modified: 星期三 22日 二月 2023 14:09:02
---

# Python 浮點精度丟失
***

>[!info]+
>cos(90 <sup>o</sup> ) 不為 0
>
>因為float會掉精確度，所以cos出來的數不是完整的0，但無限接近0
>可以使用round來四捨五入
>[詳細資料](https://stackoverflow.com/questions/13260296/python-cos90-and-cos270-not-0)

```python
import math
x = math.pi / 2
y = math.cos(x)
print(y)# 不是輸出 0.0
print(round(y, 7))  
```

### 解決方法:
精度丟失並不大，小數點好幾位以後，可用四捨五入取捨

[座標移動](https://www.youtube.com/watch?v=3DeW-7vbc50)