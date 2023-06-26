---
tags: 
aliase: 
created: 2023-02-01 09:36
modified: 星期三 1日 二月 2023 09:36:17
---

# List 接口
***
>interface 街口

```java
package isdouble;

public interface List<E> {
	static final int ELEMENT_NOT_FOUND = -1;
	E get(int index);
	E set(int index, E element);
	void add(E element);	
	void add(int index, E element);	
	E remove(int index);
	void clear();
	boolean isEmpty();
	int indexOf(E element);
	boolean contains(E element);
	int size();
}
```
