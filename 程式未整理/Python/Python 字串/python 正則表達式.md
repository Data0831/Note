---
tags: python 
aliase: 
created: 2023-02-22 14:13
modified: 星期三 22日 二月 2023 14:46:28
---

# python 正則表達式
***

<iframe width="560" height="315" src="https://www.youtube.com/embed/l1MAW1z641E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- re.search()
- group -> re.obj
- sub -> re.obj
- findall -> re.obj
- split -> re.obj
- compile -> re.obj

## search
`re.search(pattern, string) -> re.obj`
```python
import re
pattern1 = "dog"
pattern2 = "bird"
string = "dog runs to cat"
match = re.search(pattern1, string)
print(match)
```

>[!col]+
>|衍伸函式|解釋|
>|---|---|
>|.start|  |
>|.end|  |
>|.span|符合字串範圍|
>|.group|符合字串|
>>[!col]+
>若有匹配到字串回傳，re.obj，沒有則還傳None

```python
txt = """
dog runs to cat.
I run to dog
"""
print(re.search(r"^I", txt, flags=re.M))
# re.M 若多行輸入，將每行看做一個獨立的句子
```

## r-string
`syntax:r"[]"`
```python
ptn = r"r[au]n"
print(re.search(ptn, "dog runs to cat"))
```
r-string是正則表達式的重點，可以配合中括號做一些特殊用途
[0-9a-z]
[A-Z]
`syntax:r"/D"`
```python
ptn = r"r/Dn"
print(re.search(ptn, "dog runs to cat"))
```
也可以使用特殊字符 `/` + 英文字母，與中括號有類似效果
詳細資料請看[w3shool](https://www.w3schools.com/python/python_regex.asp)

## .group()
`syntax:r"()"`
```python
match = re.search(r"(\d+), Date: (.+)", "ID: 021523, Date: Feb/12/2017")
print(match.group(1))
```
group可以與括號做對應(index)
 
`syntax:r"(?P<idname>)"`
```python
match = re.search(r"(?P<id>\d+), Date: (?P<date>.+)", "ID: 021523, Date: Feb/12/2017")
print(match.group("id"))
print(match.group("date"))
```
group可以做對index設定id
 
## findall
`syntax: list(str ele) = re.findall(pattern, string)`
```python
print(re.findall(r"(run|ran)", "run ran ren"))
```
## sub
`syntax: str = re.sub(pattern, rep-string, src-string)`
```python
print(re.sub(r"(run|ran)", "catches", "dog runs to cat"))
```
將字串替換並回傳
## spilt
`syntax: list(str ele) = re.spilt(pattern, string)`
```python
print(re.spilt(r"[.;\.]","a;b,c.d;e"))
```
## compile
`syntax: re.obj = re.compile(pattern)`
```python=
compile_re = re.compile(r"r[ua]n")
print(compile_re.search("dog ran to cat"))
```

### 保留字串
**EXAMPLE:**
```python=
import re
def solution(s):
    return re.sub('([A-Z])', r' \1', s)
# 加入\1可以保留被替換的字串
```


## 題目

>[!info]+ 尋找email
>判斷txt檔裡每行的字串是否符合email規則

```txt=
1234@@asds
stu233@gmail.com
asdasf4g4s8e4fs
xui7_2@yahoo.com
sd488__@21
```

```python
import re
with open("file.txt", "r") as infile:
    data = infile.read().split()
    emails = []
    match = r"[0-9a-zA-Z_]+@+\w+.com"
    for row in data:
        string = re.search(match, row)
        if string:
            emails.append(string)
    
    for i in emails:
        print(i)
```

