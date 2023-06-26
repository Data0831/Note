---
tags: Java
aliase: array
created: 2023-01-12 12:43
modified: 星期四 12日 一月 2023 12:43:19
---
# Java 陣列
***
# 一維陣列
```java linenos
int[] array1 = {4,5,6}; //直接使用值
int[] array2 = new int[] {4,5,6}; 
int[5] array3 = new int[5];// 只建構空間，不賦值
```

# 二維陣列
```java
int[][] array = {{2,3,3},{4,5,6}};
int[][] array = new int[][] {{2,3,3},{4,5,6}};
int[][] array = new int[5][3];
```

>[!info]+
>陣列宣告會有預設值
>詳細請參考[[Java 預設值]]

***
# 陣列迭代

```java linenos
int[][] array = {{2,3,3},{4,5,6}};
for(int[] arr : array){//使用 :
	for(int num: arr){
		System.out.println(num);
	}
}
```

```java linenos
int[][] array = {{2,3,3},{4,5,6}};
for (int i = 0; i < 2; i++) {// 使用數字i
	for (int j = 0; j < 3; j++) {
		System.out.println(array[i][j]);
	}
}
```

# 陣列複製
1. clone()
2. Arrays.copyOf
```java linenos title:"clone"
int[] array = {2,3,4} ;

int[] array1 = array.clone();
array[0] = 3;

for(int num:array1) 
	System.out.println(num);
```
```result
2
3
4
```

```java linenos title:"Arrays.copyOf"
//import java.util.Arrays;
int[] Array = {1, 2, 3, 4, 5};
int[] Array2 = Arrays.copyOf(Array, Array.length);

Array[0] = 3;
for(int num:Array2) {
	System.out.println(num);
}
```
