---
tags: C++
aliase: 
created: 2023-01-14 10:19
modified: 星期六 14日 一月 2023 10:19:25
---

# C++ 陣列
***
# 一維陣列
```cpp linenos title:"靜態宣告"
int array1[10];//靜態宣告
int array2[10] = {1,2,3};
int array3[] = {};
```

```cpp linenos title:"動態宣告"
int *array1 = new int[10]; //動態宣告
int *array2 = new int[10]{1,2,3,4,5}; //動態宣告 並賦值 (只適用於C++11及以上)
int *array3 = new int[5](); //動態宣告 初始為0
delete[] array1;//釋放內存
delete[] array2;
delete[] array3;
```

---
# 二維陣列

```cpp linenos title:"靜態宣告"
int array1[10][5];//靜態宣告
int array2[3][3] = {{1,2,3},{4,5,6}};
int array3[][3] = {{1,2,3},{4,5,6}};
int array3[10][5] = {};//歸0
```

```cpp linenos title:"動態宣告"
int **array = new int*[10]; //宣告二維陣列

for (int i = 0; i < 10; i++) 
    array[i] = new int[5]();//宣告5個int 空間初始化0，並把地址存入 array[i]

for (int i = 0; i < 5; i++) // 釋放記憶體
    delete[] array[i];// 刪除連續的數字空間
delete[] array;// 刪除連續的一維地址空間
```

---

## new 進階
>[!note]+
>若*記憶體不夠*時使用new會回傳**nullptr**，申請記憶體空間時，要記得做**NULL check**

```cpp linenos title:"Null check"
int* ptr = new int[100];
if (ptr == nullptr) {
    // 分配失敗的處理
} else {
    // 成功分配的處理
}
```

>[!info]+ new
>動態宣告**只能使用指標**，因為 new 回傳的是地址值
>`type* a = new type[size]`

>[!info]+ delete 與 delete[]
>`delete[]` 代表刪除連續的內存
>`delete` 代表刪除單個內存
>`delete[] ptr`: ptr為指向分配的記憶體的指標，將ptr作為參數傳遞給 `delete`，並且確保**該指標未被使用**，`delete` 釋放記憶體塊後，該指標不再是有效的，應該將其**設置為 nullptr**，以避免出現野指針。

```cpp linenos title:"delete 示例"
int *num = new int();
delete num;
```
### new 賦值
```cpp linenos title:"new 示例"
double *a = new double(7.0);
int *arr = new int[10]{1,2,3,4,5}; 
```

### delete 
delete後應將*指標設為nullptr*
```cpp linenos title:"delete 示例"
double *a = new double(7.0);
delete a;
a = nullptr;
```

***
# 陣列迭代
```cpp linenos title:"一維"
int array[3] = {1,2,3};
for (int num:array) {
	cout << num;
}
```

```cpp linenos title:"二維"
int array[3][3] = {{1,2,3},{4,5,6}};
for (int i = 0; i < 2; i++) {// 使用數字i
	for (int j = 0; j < 3; j++) {
		cout << array[i][j];
	}
}
```

# 陣列歸0
1. for 迴圈
2. memset 函式
3. 在初始化時設定 `={}`、`[]()`

```cpp linenos title:"memset 示例"
#include <cstring>
int arr[10];
memset(arr, 0, sizeof(arr));
```

```cpp linenos title:"初始化 示例"
int arr1[10]={}; // 靜態
int *arr2 = new int[10]();// 動態 加上()
```

# 陣列複製
1. for 迴圈
2. memcpy 函式
```cpp linenos title:"memcpy 示例"
int* arr = new int[5];
int temp[5] = {1, 2, 3, 4, 5};
memcpy(arr, temp, 5 * sizeof(int));
```
