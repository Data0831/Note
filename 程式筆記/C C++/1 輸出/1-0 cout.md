---
tags: C++
aliase: 
created: 2023-06-15 06:48
modified: 星期四 15日 六月 2023 06:50:16
---

# 1-0 cout
***

>[!info]+ cout class
>std::ostream& **cout** << sample;
>回傳值: **std::ostream&** cout
>operator: <<

- format 的格式:
```cpp
cout << [specifier0] << [specifier1] << ... << [specifierN] << Value;
```
>cout 可以有多個specifier，並且大部分specifier一但設定**之後的輸出都將會被應用**，setw()除外

- EX:
```cpp
string str = "123456";
cout.write(str.c_str(), 3); // str.cstr() 轉成 char*
```
```result
  123 
```

---

## cout flag 的使用
- cout.setf(ios::flag)
- cout << setiosflags(ios::flag)

```cpp title:"使用flag"
cout << scientific << 73.82 <<endl; // 正常使用
cout << setiosflags(ios::scientific) << 3.7; //啟用flag 
cout.setf(ios::scientific); //透過成員啟用flag 
```

```cpp title:"取消flag"
// 少部分flag剛好有相反值可以取消
cout << resetiosflags(ios::scientific) << 3.7; //啟用flag 
cout.unsetf(ios::scientific); //透過成員啟用flag 
```
> 要使用多個flag可用'|'作連接
- cout.setf(ios::oct|ios::showpos)
- cout << setiosflags(ios::oct|ios::showpos)


---
## 格式控制符 specifier

|specifier|作  用|   |
|---|---|---|
|\*dec|以十進制形式輸出整數||
|hex|以十六進制形式輸出整數|
|oct|以八進制形式輸出整數|
|fixed|以普通小數形式輸出浮點數(**6位**)|
|scientific|以科學計數法形式輸出浮點數|
|left|左對齊，即在寬度不足時將填充字符添加到右邊|
|\*right|右對齊，即在寬度不足時將填充字符添加到左邊|
|setbase(b)|設置輸出整數時的進制，b=8、10 或 16|
|setw(w)|指定輸出寬度為 w 個字符，或輸人字符串時讀入 w 個字符|
|setfill(c)|在指定輸出寬度的情況下，輸出的寬度不足時用字符 c 填充（默認情況是用空格填充）|
|setprecision(n)|設置輸出浮點數的精度為 n。 <br>  <br>在使用非 fixed 且非 scientific 方式輸出的情況下，n 即為有效數字最多的位數，如果有效數字位數超過 n，則小數部分四捨五人，或自動變為科學計 數法輸出並保留一共 n 位有效數字。 <br>  <br>在使用 fixed 方式和 scientific 方式輸出的情況下，n 是小數點後面應保留的位數。 |
|setiosflags(flag)|將某個輸出格式標誌置為 1|
|resetiosflags(flag)|將某個輸出格式標誌置為 0|
|boolapha|把 true 和 false 輸出為字符串||
|\*noboolalpha|把 true 和 false 輸出為 0、1|
|showbase|輸出表示數值的進制的前綴|
|\*noshowbase|不輸出表示數值的進制.的前綴|
|showpoint|總是輸出小數點|
|\*noshowpoint|只有當小數部分存在時才顯示小數點|
|showpos|在非負數值中顯示 +|
|\*noshowpos|在非負數值中不顯示 +|
|\*skipws|輸入時跳過空白字符|
|noskipws|輸入時不跳過空白字符|
|uppercase|十六進制數中使用 A~E。若輸出前綴，則前綴輸出 0X，科學計數法中輸出 E|
|\*nouppercase|十六進制數中使用 a~e。若輸出前綴，則前綴輸出 0x，科學計數法中輸出 e。 |
|internal|數值的符號（正負號）在指定寬度內左對齊，數值右對齊，中間由填充字符填充。 |


---
# 參考
**外部**
- [cout](http://c.biancheng.net/view/275.html)

---
**內部**

C: [[1.0 printf]]
- 
