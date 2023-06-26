---
tags: Queue
aliase: 
created: 2023-02-01 09:53
modified: 星期三 1日 二月 2023 09:53:14
---

# Queue
***

```java
package single;

import isdouble.LinkedList;

public class Queue<E> {
	private LinkedList<E> list = new LinkedList<>();

	public int size() {
		return list.size();
	}

	public boolean isEmpty() {
		return list.isEmpty();
	}

	public void enQueue(E element) {
		list.add(element);
	}

	public E deQueue() {
		return list.remove(0);
	}

	public E front() {
		return list.get(0);
	}
}
```
