# Python 檔案處理模組
***


# csv write/read

```csv=
姓名,縣市,住址
陳大明,台北市,汀州路四段88號
張小華,臺北市,和平東路一段162號
李國華,台北市,復興南路一段6號8樓
朱志清,台中市,大仁路38巷4號5F
朱婷婷,台中市,中港路29號2樓
周杰倫,台南市,中港路四段390-1號
劉德明,高雄市,三多路49巷2弄1號14F
紀小月,台東市,中台五路95號

```

```python
import csv

with open("addr.csv", "r") as infile:
    data = list(csv.DictReader(infile))
    # csv.DictReader wiil load file as dict type

new_title = ["Name", "City", "Addr"]
with open("new_addr.csv", "w", newline="") as outfile:
    write = csv.DictWriter(outfile, fieldnames=data[0].keys())
    write.writeheader()
    # write.writerows()
    for row in data:
        write.writerow(row)
        # 自動加換行符號
```

<pre>
csv.DictReader(outfile)
csv.DictWriter(outfile, fieldnames=)
write.writerow(row)
row 一行列表
write.writerow(data)
data 整筆資料
</pre>