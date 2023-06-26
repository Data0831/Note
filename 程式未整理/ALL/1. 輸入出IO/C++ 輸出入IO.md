---
tags: C++
aliase: 
created: 2023-02-21 15:18
modified: 星期二 21日 二月 2023 15:18:38
---


---
# Cin

>[!success]+
>cin做`>>`運算時返回**&cin物件**，若一次讀取成功時(已經沒有`>>`)回傳**true**，讀取失敗回傳**false**
>當讀取的資料型別與指定的型別不同時，`cin` 會發生錯誤，在這種情況下，`cin` 的返回值會是 **false**， 若cin讀取到EOF也會返回**false**

```cpp linenos title:"讀取失敗"
int main() {
    int num;
    while (cin >> num) {// 輸入"123a",先讀取123， a因為不是整數所以會回傳false，跳出迴圈
        cout << "Read number: " << num << endl;
    }
}

```
```result
Read number: 123
```

上方程式碼中的 while 迴圈條件 `cin >> num` 會先試著從標準輸入中讀取一個數字，並將讀取到的數字存入 `num` 變數中。如果讀取成功，則會返回一個值為 true 的布林值，代表讀取成功。而迴圈條件判斷的運作方式為，只有當該布林值為 true 時，才會繼續執行迴圈內的指令，否則跳出迴圈。

因此，當使用者不斷地在標準輸入中輸入數字，每次敲擊 Enter 鍵後，迴圈會一直執行下去，並且每次都會讀取下一個數字。直到使用者輸入非數字的內容，或者在標準輸入中輸入 EOF (End-of-File) 符號（通常是在鍵盤上按下 Ctrl+D 或 Ctrl+Z），這時讀取操作會失敗， `cin` 會返回一個值為 false 的布林值，迴圈會因此停止執行。

## 檢測EOF或fail
>[!info]+
>fail(): 若cin讀取型態無法轉換，如字母轉數字，fail()會設定成true (EOF發生時fail也為true)
>eof(): 讀取到檔案末尾，eof()會設定成true 

```cpp linenos title:"eof 與 fail"
int main() {
    int num;
    while (cin >> num) //當使用 `cin` 讀取整數時，若讀取到非整數的字元（例如 `a`）時，`cin` 會發生錯誤，並且  返回 false
        cout << "Read number: " << num << endl;
    
    if (cin.fail()) //檢查錯誤標誌
        cout << "Input failed" << endl;
    
    if (cin.eof()) //檢查是否已經到達檔案結尾
        cout << "Input EOF" << endl;
}
```
```result prompt:"輸出"
^Z
```
```result prompt:"結果"
Input failed
Input EOF
```

>[!info]+
>`cin`會將失敗的狀態設為`failbit`。此時，`cin.fail()`會返回`true`，表示讀取失敗

>[!info]+
當讀取到結尾（EOF）時，`cin` 將自動設置其內部的 eof 標誌（eofbit），表示到達了輸入流的結尾。使用 `cin.eof()` 函數可以檢測 eof 標誌是否被設置。需要注意的是，**EOF 是一個特殊的字符**（通常是 Ctrl+Z 或 Ctrl+D），**而不是一個數值**

### 關於EOF
>[!info]+
>在C/C++中，EOF代表著"End Of File"，並不等同於0。EOF是一個符號常量，通常定義在stdio.h或cstdio標頭檔中，其值為-1，表示文件或標準輸入流已經結束。在讀取檔案或從鍵盤輸入時，當達到檔案結尾或按下Ctrl+D（Linux/Unix）或Ctrl+Z（Windows）時，EOF將被返回。

---
## cin.get

>[!info]+ 語法
>cin.get()
>`cin.get(char* s, streamsize n, char delim)`
>`cin.get(char& c)`

1. `cin.get(char* s, streamsize n, char delim)`:字符讀取並存儲到的`s`中，直到<mark style="background: #FFB86CA6;">讀取了</mark>`n-1`<mark style="background: #FFB86CA6;">個字符</mark>、遇到了分隔符`delim`（默認是換行符`\n`）或者到達了輸入流的末尾。讀取到的字符會*包括分隔符*（如果有的話），*但不會將其存儲到*`s`中。此外，`cin.get()`會在`s`的末尾添加一個空字符（`\0`），以標記字符串的結束。
    
2.  `cin.get(char& c)`：這種形式的`cin.get()`會讀取一個字符並將其存儲到`char`類型的變數`c`中。如果需要讀取多個字符，可以將其放在一個循環中，並在循環中進行相應的處理。
    
```cpp linenos title:"示例"
char str[11];
// 字符串長度為10，最後一個字符留給空字符'\0' 
cin.get(str, 11); // 讀取10(n-1)個字符（包括分隔符），並在末尾添加空字符 
cout << str << endl; 
// 輸出讀取到的字符串
```


需要注意的是，`cin.get()`並不會自動忽略分隔符，如果不需要分隔符，需要額外進行處理。例如，以下代碼示範了如何使用`cin.get()`來讀取一個長度為10的字符串，並且忽略其中的分隔符：

```cpp linenos title:"額外處理分隔符"
int main() {
	char str[11];
	for (int i = 0; i < 10; i++) {
		char c;
		cin.get(c); // 逐個讀取字符     
		if (c == '\n') break; // 如果讀到換行符，跳出循環     
		str[i] = c; // 將字符存儲到字符串中 
	}
	str[10] = '\0'; // 添加空字符 
	cout << str << endl;
}
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

### cin.get 吃掉空格
```
cin >> a; // 輸入10 => 10被讀取 stdin裡剩下'\n'
cin.get() // 讀取'\n' stdin="" 
```


## 文件末尾判斷EOF
>[!info]+
>在 C++ 中，我們可以使用 cin 的 eof() 函數來判斷是否到達文件末尾。當 cin.eof() 返回 true 時，表示已經到達了文件末尾 `ctrl + z`

在讀取輸入時，我們可以將 cin 作為判斷條件，循環讀取輸入直到到達文件末尾。例如：
```cpp linenos 
int num;
while (cin >> num) {
    // 處理
}
```

在此代碼中，cin >> num 語句會嘗試讀取下一個整數，並返回 cin 對象。當讀取失敗時（比如到達文件末尾），cin 對象會被視為 false，從而跳出循環。






