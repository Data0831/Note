---
tags: 
aliase: 
created: 2023-02-01 09:23
modified: 星期三 1日 二月 2023 09:23:32
---

# Array
***
> Array first version


```java
package single;
// no optimization
import isdouble.AbstractList;
@SuppressWarnings("unchecked")

public class ArrayList<E> extends AbstractList<E> {
	private E[] elements;
	private static final int DEFAULT_CAPACITY = 10;

	public ArrayList() {
		elements = (E[]) new Object[DEFAULT_CAPACITY];
	}

	public ArrayList(int size) {
		int capacity = (size > DEFAULT_CAPACITY) ? size : DEFAULT_CAPACITY;
		elements = (E[]) new Object[capacity];
	}

	private void ensureCapacity(int capcity) {
		int oldCapacity = elements.length;
		if (capcity < oldCapacity)
			return;

		int newCapacity = oldCapacity + (oldCapacity >> 1);
		E[] newElements = (E[]) new Object[newCapacity];

		for (int i = 0; i < size; i++) {
			newElements[i] = elements[i];
		}
		elements = newElements;
		System.out.println("capacity:" + oldCapacity + " -> " + newCapacity);
	}

	private void trim() {
		int oldCapacity = elements.length;
		if (size >= (oldCapacity >> 2) || oldCapacity < 2 * DEFAULT_CAPACITY)
			return;

		int newCapacity = oldCapacity >> 1;
		E[] newElements = (E[]) new Object[newCapacity];

		for (int i = 0; i < size; i++) {
			newElements[i] = elements[i];
		}
		elements = newElements;
		System.out.println("capacity:" + oldCapacity + " -> " + newCapacity);
	}

	@Override
	public E get(int index) {
		rangeCheck(index);
		return elements[index];
	}

	@Override
	public E set(int index, E element) {
		rangeCheck(index);
		E oldElement = elements[index];
		elements[index] = element;
		return oldElement;
	}

	@Override
	public void add(int index, E element) {
		rangeCheckForAdd(index);
		ensureCapacity(size + 1);
		for (int i = size; i > index; i--) {
			elements[i] = elements[i - 1];
		}
		elements[index] = element;
		size++;
	}

	@Override
	public E remove(int index) {
		rangeCheck(index);
		E old = elements[index];

		for (int i = index + 1; i < size; i++) {
			elements[i - 1] = elements[i];
		}

		elements[size--] = null;
		trim();
		return old;
	}

	@Override
	public void clear() {
		for (int i = 0; i < size; i++)
			elements[i] = null;

		size = 0;
		trim();
	}

	@Override
	public int indexOf(E element) {
		if (element == null) {
			for (int i = 0; i < size; i++) {
				if (element == elements[i]) {
					return i;
				}
			}
		} else {
			for (int i = 0; i < size; i++) {
				if (element.equals(elements[i])) {
					return i;
				}
			}
		}

		return ELEMENT_NOT_FOUND;
	}

	public String toString() {
		StringBuilder string = new StringBuilder();
		string.append("size: ").append(size).append("  [");
		
		for (int i = 0; i < size; i++) {
			if (i != 0)
				string.append(",");
			string.append(elements[i]);
		}
		string.append("]");

		return string.toString();
	}
}

```
