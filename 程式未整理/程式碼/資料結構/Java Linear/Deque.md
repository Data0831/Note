---
tags: Deque
aliase: 
created: 2023-02-01 09:54
modified: 星期三 1日 二月 2023 09:54:09
---

# Deque
***

```java
package single;

import isdouble.LinkedList;

public class Deque<E> {
	private LinkedList<E> list = new LinkedList<>();

	public int size() {
		return list.size();
	}

	public boolean isEmpty() {
		return list.isEmpty();
	}

	public void enQueueFront(E element) {
		list.add(element);
	}

	public void enQueueRear(E element) {
		list.add(0, element);
	}

	public E deQueueFront() {
		return list.remove(0);
	}

	public E deQueueRear() {
		return list.remove(list.size() - 1);
	}

	public E front() {
		return list.get(0);
	}

	public E rear() {
		return list.get(list.size() - 1);
	}
}
```
