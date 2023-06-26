---
tags: C++ 輸入
aliase: 
created: 2023-06-16 23:22
modified: 星期五 16日 六月 2023 23:22:42
---

# 2-0 cin
***

>[!info]+ cin class
>std::istream& **cin** >> sample;
>回傳值: **std::istream&** cin
>operator: >>

## cin的讀取判斷: 
```cpp 
while (cin >> num) {
// 輸入"123a",先讀取123， a因為不是整數所以會回傳false，跳出迴圈
	cout << "Read number: " << num << endl;
}//可以一直輸入直到讀取錯誤或是檔案末尾
```

>[!success]+ 隱式轉換的條件判斷
>cin、cout 讀取可做為條件式，當放入()中做判斷時會**隱式轉換**，若讀取成功時為**true**，讀取失敗為**false**
>false: *型別不同*或*檔案末尾*(EOF)

條件操作:
```cpp title:"錯誤" highlight:"1" 
if ((cin >> a)==true) cout << "T";//錯誤: 編譯器還沒做隱式轉換就先做條件操作
```

```cpp title:"正確"
if (cin >> a)  cout << "T";// 編譯器會做隱式轉換
else cout << "F";

if (bool(cin >> a) == true)  cout << "T";// 強制轉換
else cout << "F";
```

---

也可以透過成員函數做判斷: 
>[!info]+
>bool cin.fail(): 若cin讀取**型態無法轉換**(如字母轉數字)或**EOF**，fail()會設定成true 
>bool cin.eof(): 讀取到檔案末尾，eof()會設定成true 

```cpp linenos title:"eof 與 fail"
while (!(cin >> x)) {
// 如果讀取成功: false 讀取失敗 true
	if (cin.eof()) cout << "EOF\n";
	// 如果為EOF: true
	if (cin.fail()) {
	// 如果為EOF或形態不匹配: true
		cout << "fail\n";
		break;
	}
}
```
```result prompt:"輸出"
a
// 隔開
^Z^Z^Z
```
```result prompt:"結果"
fail
// 隔開
EOF
fail
```

---
## cin.get
>[!info]+ 
>int get(): 回傳整數對應的ASCII，讀至末尾回傳EOF(-1)
>std::istream& get(&ch): 讀取成功為true，讀取失敗(EOF)為false
>
>std::istream& cin.get(char* s, streamsize n, (optional)char delim)
>回傳: 讀取成功為true，讀取失敗(EOF)為false
>delim: 終止符，默認為'\n'
>結束條件: `size-1`, `\n`, `delim`, `EOF` 
>
>**delim會殘留在stdin**，會在最後補上'\0'

```cpp linenos title:"讀取字元"
char a = cin.get();
cin.get(a);
```

```cpp linenos title:"讀取字串"
char str[11];
cin.get(str, 11); // 讀取10(n-1)個字符（包括分隔符），並在末尾添加空字符 
// stdin不會殘留delim，但delim也不會被儲存至字串
```


### cin.get() 單個讀取
使用者輸入1234中間沒有空格，我該如何使用cin讀取分別讀取4次: 1，2，3，4

1. 讀成字串後對字串做單位處理
2. 讀成一個個字元做單位處理

可以使用 `cin.get()` 函數來逐個讀取輸入中的字符，再將其轉換為整數。具體代碼如下：

```cpp linenos 
#include <iostream> 

using namespace std;

int main() {
	int num[4];
	char tmp;

	for (int i = 0; i < 4; i++) {
		cin.get(tmp);// 使用tmp暫存
		num[i] = tmp - '0';//轉成整數後再存入陣列
		cout << num[i] << ' ';
	}
	cout << endl;
	return 0;
}
```



## cin.getline()





**delim不會殘留在stdin**但delim也不會被儲存至字串