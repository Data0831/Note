---
tags: Java 
aliase: 
created: 2023-02-22 13:04
modified: 星期三 22日 二月 2023 13:04:43
---

# Java 模板
***
## 模板  泛型
```java
ArrayList<Person> arr = new ArrayList<>();
```

```java
public class ArrayList<E>{
	public ArrayList() {
		elements = (E[]) new Object[DEFAULT_CAPACITY];
	}

	public ArrayList(int size) {
		int capacity = (size > DEFAULT_CAPACITY) ? size : DEFAULT_CAPACITY;
		elements = (E[]) new Object[capacity];
	}
}
```
>這裡的elements陣列裡存的是地址，只要儲存物件就是地址，因為我們無法得知每個物件的大小，儲存地址可以簡化麻煩。
>透過模板可以使用不同類型的物件
***
