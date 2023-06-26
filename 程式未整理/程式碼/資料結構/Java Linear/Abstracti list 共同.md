---
tags: 
aliase: 
created: 2023-02-01 09:35
modified: 星期三 1日 二月 2023 09:35:31
---

# Abstractilist 共同
***
># Abstract抽象類

```java
package isdouble;

public abstract class AbstractList<E> implements List<E> {
	protected int size;
	
	protected void rangeCheck(int index){
		if(index < 0 || index >= size)	
			throw new IndexOutOfBoundsException("size: " + size + "  index: " + index);
	}
	
	
	protected void rangeCheckForAdd(int index){
		if(index < 0 || index > size)	
			throw new IndexOutOfBoundsException("size: " + size + "index: " + index);
	}
	
	public void add(E val) {
		add(size, val);
	}
	
	public boolean isEmpty() {
		return size == 0;
	}
	
	public int size() {
		return size;
	}
	
	public boolean contains(E element) {
		return indexOf(element) != ELEMENT_NOT_FOUND;
	}
	
}
```
