---
tags: Python
aliase: "data analysis"
created: 2022-12-28 15:54
modified: 星期五 13日 一月 2023 09:19:56
---

# Python 資料分析
***
# matplot成績曲線圖


**學生成績** 
    
```csv=
Name,Hw1,Hw2,Hw3,Exam1,Exam2,Final
Tom,100,90,100,80,85,91.5
Jane,90,90,100,90,60,83.5
Mike,30,40,100,50,70,66
Tim,60,70,90,80,90,83
Jason,99,99,80,99,80,93.3
Ellen,88,88,100,88,60,82.6
Jessie,100,100,100,0,100,80
Linda,100,0,100,100,100,100

```


**程式碼：**
    
```python
import matplotlib.pyplot as plt

with open("學生成績.csv", "r") as infile:
    data = infile.read().split()

captions = data[0].split(",")
stus = []

for row in data[1:]:
    person = row.split(",")
    # tmp = 
    stus.append([person[0]] + [float(i) for i in person[1:]])

for stu in stus:
    name = stu[0]
    scores = stu[1:]
    plt.clf()
    plt.plot(scores, marker="o")
    plt.title(name)
    plt.xticks(range(len(scores)), captions[1:])
    plt.xlabel("Items")
    plt.ylabel("Scores")
    plt.ylim(0, 110)
    plt.tight_layout()
    plt.savefig(name+".png")
    # plt.show

```



<pre>
plt.clf: 創建新的圖
plt.plot(分數列表, marker="v")# marker 表現形態
plt.title: 標題
plt.ylim: y值範圍
plt.tight_layout():限制繪畫範圍在圖內
plt.savefig(name+".png"):存檔
</pre>

# Python pandas


## read csv

`syntax: re.obj = re.search(pattern, string)`

**EXAMPLE:**
```python=
df = pd.read_csv("stock.csv", encoding= , skiprows = int, header=None, names=["goajsfi", "Adasd"])
print(df)
```
**指定表單**
```python=
df = pd.read_csv("stock.csv", "stock")
print(df)
```
默認參數
```python=
pandas.read_csv(filepath_or_buffer, sep=',', delimiter=None, header='infer', names=None, index_col=None, usecols=None, squeeze=False, prefix=None, mangle_dupe_cols=True, dtype=None, engine=None, converters=None, true_values=None, 
                false_values=None, skipinitialspace=False, skiprows=None, 
                nrows=None, na_values=None, keep_default_na=True, na_filter=True, 
                verbose=False, skip_blank_lines=True, parse_dates=False, 
                infer_datetime_format=False, keep_date_col=False, date_parser=None, 
                dayfirst=False, cache_dates=True, iterator=False, chunksize=None, 
                compression='infer', thousands=None, decimal='.', lineterminator=None,
                quotechar='"', quoting=0, escapechar=None, comment=None, 
                encoding=None, dialect=None, error_bad_lines=True, 
                warn_bad_lines=True, skipfooter=0, doublequote=True, 
                delim_whitespace=False, low_memory=True, memory_map=False, 
                float_precision=None)
```

### na_values去除不要的值
```csv=
股票代碼,每股盈餘,營收,價格,創始人
GOOG,23.49,48.82,1151,Larry Page
WMT,1.76,55.04,95.64,n.a.
MSFT,-1,52.5,111.14,Bill Gates
BABA,數據缺失,43.16,147.97,Jack Ma
TCEHY,1.31,-1,n.a.,Pony Ma
```

```python=
df = pd.read_csv("stock.csv", na_values=["數據缺失", "n.a."])
```

```python=
df = pd.read_csv("stock.csv", na_values={
    "每股盈餘":["數據缺失", "n.a."],
    "創始人":["數據缺失", "n.a."],
    "營收":["數據缺失", "n.a.", -1]
})
```
### 儲存csv
```python=
df.to_csv("new.csv", encoding="utf-8_sig", index=False)
```
要加encoding, 必須用"utf-8_sig"

***
### excel read output
```python=
pd.set_option('display.unicode.east_asian_width', True)
df = pd.read_excel("stock.xlsx", na_values={
    "每股盈餘":["數據缺失", "n.a."],
    "創始人":["數據缺失", "n.a."],
    "營收":["數據缺失", "n.a.", -1]
})
print(df)
df.to_excel("new.xlsx", index=False)
```
使用前要安裝==openpyxl==
read不能指定encoding



### 表格對齊與美化

```python=
# pd.set_option('display.unicode.ambiguous_as_wide', True)
# pd.set_option("display.width", 180)
# 上兩行不知何用途
pd.set_option('display.unicode.east_asian_width', True)
```
當中英文混合時會出現無法對其狀況，使用set_option('display.unicode.east_asian_width', True)可以將中文字對齊






