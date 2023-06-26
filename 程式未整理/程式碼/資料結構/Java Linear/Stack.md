---
tags: Stack
aliase: 
created: 2023-02-01 09:51
modified: 星期三 1日 二月 2023 09:51:57
---

# Stack
***

```java
package single;

public class Stack<E> {
	private ArrayList<E> list = new ArrayList<>();

	public Stack() {
	}

	public int size() {
		return list.size();
	}

	public boolean isEmpty() {
		return list.isEmpty();
	}

	public void push(E element) {
		list.add(element);
	}

	public E pop() {
		return list.remove(list.size() - 1);
	}

	public E top() {
		return list.get(list.size() - 1);
	}
}
```
