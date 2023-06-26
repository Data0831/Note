---
tags: C 
aliase: 
created: 2023-03-29 19:06
modified: 星期三 29日 三月 2023 19:06:06
---

# C 陣列
***
# 一維陣列
```cpp linenos title:"靜態宣告"
int array1[10];//靜態宣告
int array2[10] = {1,2,3};
int array3[] = {};
```

```cpp linenos title:"動態宣告"
int *array1 = (int*)malloc(10 * sizeof(int)); //動態宣告長度為10的陣列且未賦值
int *array2 = (int*)calloc(10, sizeof(int)); //動態宣告 初始為0
int *array3 = (int*)realloc(array2, 20 * sizeof(int));// 創建長20單位的空間，並將array2的值複製過來，index10以後的值設為0
free(array1);//釋放內存
// free(array2); 不用free array2 因為realloc會處理原本array2位置
free(array3);
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
int **array = (int**)malloc(10 * sizeof(int*)); //宣告二維陣列

for (int i = 0; i < 10; i++) 
    array[i] = (int*)calloc(10, sizeof(int));//宣告5個int 空間初始化0，並把地址存入 array[i]

for (int i = 0; i < 5; i++) // 釋放記憶體
    free(array[i]);// 刪除連續的數字空間
free(array);// 刪除連續的一維地址空間
```

---

## 動態宣告進階
>[!note]+
>若*記憶體不夠*時會回傳NULL，申請記憶體空間時，要記得做**NULL check**

>[!info]+
>`void* malloc(size_t size))`
>`void* calloc(amount, sizeof(type))`
>`void* realloc(void* ptr, size_t size);`
>

```cpp linenos title:"Null check"
int* ptr = (int*)malloc(10*sizeof(int));
if (ptr == NULL) {
    // 分配失敗的處理
} else {
    // 成功分配的處理
}
```

>[!info]+ new
>動態宣告**只能使用指標**，因為 new 回傳的是地址值
>`type* a = new type[size]`

>[!info]+ free
>free(ptr) ptr為指向分配的記憶體的指標，將ptr作為參數傳遞給 `free()`，並且確保**該指標未被使用**，`free()` 釋放記憶體塊後，該指標不再是有效的，應該將其**設置為 NULL**，以避免出現野指針。

```cpp linenos title:"free 示例"
int *num = (int*)malloc(sizeof(int));
delete num;
```
### 動態賦值
```cpp linenos title:"new 示例"
int *arr = (int*)malloc(10*sizeof(int));
for(int i=0;i<10;i++){
	arr[i] = i+1;//1~10
}
```
### free 
free後應將*指標設為NULL*
```cpp linenos title:"free 示例"
double *a = new double(7.0);
free(a);
a = NULL;
```

### realloc 
>[!info]+
>`realloc()` 函式可以在動態內存分配時重新調整已經分配的內存塊的大小
>`void* realloc(void* ptr, size_t size);`

參數：指向原內存塊的指針 `ptr` 和重新調整後的大小 `size`。如果 `ptr` 為 `NULL`，那麼該函式的行為類似於 `malloc()` 函式，即它將分配一塊大小為 `size` 字節的內存。如果 `size` 為 0，那麼該函式的行為類似於 `free()` 函式，即它將釋放指針 `ptr` 所指向的內存塊。

如果函式調用成功，它將返回一個*指向新分配內存的指針*，或者如果無法滿足請求的內存量，則返回 `NULL`。請注意，`realloc()` 函式可能會在**新位置**重新分配內存塊(也可能跟**舊位置**一樣，看編譯器如何處理)，因此新內存塊的地址可能與原內存塊不同(或相同)。如果新分配的內存塊大小大於原內存塊大小，則新分配的空間中的所有字節都將被**初始化為零**。

| 條件                  | 處理                                      | 
|:--------------------|:----------------------------------------|
| 新位置`==`舊位置，新內存&gt;舊內存 | 前面部分不動，後面進行free()                       | 
| 新位置`==`舊位置，新內存&lt;舊內存 | 前面部分不動，後面初始化為0                          | 
| 新位置!=舊位置，新內存&gt;舊內存 | 舊內存的資料複製一部分至新內存，並對舊內存進行free()           | 
| 新位置!=舊位置，新內存&lt;舊內存 | 舊內存的資料複製全部至新內存，新內存後方初始化為0，並對舊內存進行free() |  

```cpp linenos title:"realloc示例"
#include <stdio.h>
#include <stdlib.h>
int main(){
    int* array = (int*)malloc(5 * sizeof(int));// 初始分配大小為 5 的整數數組
    for (int i = 0; i < 5; i++) array[i] = i;// 賦值 0~4
    
    int* newArray = (int*)realloc(array, 10 * sizeof(int));// 將數組大小擴展到 10
    if (newArray != NULL) {// 若分配成功內存
        array = newArray;
        for (int i = 5; i < 10; i++) array[i] = i;// 賦值 5~9
        
        for (int i = 0; i < 10; i++) printf("%d ", array[i]);
        printf("\n");
    }
    free(array);
    return 0;
}
```
```result
0 1 2 3 4 5 6 7 8 9 
```

***
# 陣列迭代

```cpp linenos title:"一維"
int array[3] = {1,2,3};
for (int i = 0; i < 3; i++) {
	printf("%d", array[i]);
}
```


```cpp linenos title:"二維"
int array[3][3] = {{1,2,3},{4,5,6}};
for (int i = 0; i < 2; i++) {// 使用數字i
	for (int j = 0; j < 3; j++) {
		printf("%d", array[i][j]);
	}
}
```

# 陣列歸0
1. for 迴圈
2. memset 函式
3. calloc

```cpp linenos title:"memset 示例"
#include <cstring>
int arr[10];
memset(arr, 0, sizeof(arr));
```

```cpp linenos title:"初始化 示例"
int arr1[10]={}; // 靜態
int *arr2 = (int*) calloc(10, sizeof(int));// 動態 
```

# 陣列複製
1. for 迴圈
2. memcpy 函式
```cpp linenos title:"memcpy 示例"
int* arr = new int[5];
int temp[5] = {1, 2, 3, 4, 5};
memcpy(arr, temp, 5 * sizeof(int));
```

---
# 陣列衰變

>[!info]+
>指的是將陣列做參數傳遞時，丟失了dimesion與size_length這兩項屬性

ex:
```cpp
int arr[10]; //size = 40 
func(arr); // sizeof(pointer) = 8
sizeof(arr);// = 48
```
^ArrayDecay

由上述例子我們可以看出
- size變了運算子把arr args偵測為指標
- int[10] 衰變成 int* 維度損失 1維 -> 0

可參考: https://wucodingroad.blogspot.com/2017/09/Cplusplus-array-decay.html
***