---
tags: Q ALL
aliase: 
created: 2023-04-29 13:14
modified: 星期六 29日 四月 2023 13:14:00
---

# Q 陣列進階
***
1. 請問以下C++程式碼是否正確？

```cpp linenos 
int *array1 = new int[10]; //動態宣告
delete array1;
```

>[!note]- Ans
>delete 只會釋放array1在index=0位置的內存，應該使用`delete[] array1;`

2. 請問以下C++程式碼是否正確？

```cpp linenos
int array2[3][3] = {{1,2,3},{4,5,6}};
for(int* arr : array){//使用 :
	for(int num: arr){
		System.out.println(num);
	}
}
```

>[!note]- Ans
>在第3行發生錯誤，此時的arr發生衰變，變成單純的指標沒有了陣列屬性