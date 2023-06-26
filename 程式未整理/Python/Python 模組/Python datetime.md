---
tags: Python 
aliase: 
created: 2023-02-22 14:18
modified: 星期三 22日 二月 2023 14:18:43
---

# Python datetime
***
- time.sleep(1.0)暫停1秒，要先import time


``` python
# datetime
import datetime
dt1 = datetime.datetime.now()
dt2 = datetime.datetime.utcnow()
dt3 = datetime.datetime.today()#本地時間
dt4 = datetime.datetime(2022,8,16,7,16,20,1615)
print(dt1.isoweekday())
# 可以輸出個別元素
# date/time/year/month/isoweekday/weekday/day/hour/minute/second/microsecond

# datetime.strftime(directive) string format time
x = datetime.datetime(2022,11,26,6,38,20,1615)
print(x.strftime("%A"))
# directive: captal is full, lower is short
```

- %a %A week 
- %w weekday:num 
- %d day:0~31- %b %B month name: Dec 
- %m: mon:day
- %y %Y year
- %I %H hour 0~12 0~24- %p am/pm
- %M minute
- %S second
- %f microsecond
- %j daynumber of day 今年的第幾天
- %U %W week number of year sun/monday as first day
- %c %x %X local version of date and time/ date/ time
- %C century 20th
- %`%` character %
- %G %u %V iso 8601 year/weekday 1-7/ weeknumber 1-53