---
tags: 
aliase: 
created: 2023-02-01 09:20
modified: 星期三 1日 二月 2023 09:20:02
---

# Array
***
>Arraylist java Capacity expand optimization

```java
package single;
// first sudo index

import isdouble.AbstractList;
@SuppressWarnings("unchecked")

public class ArrayList2<E> extends AbstractList<E> {
	private int first = 0;
	private E[] elements;
	private static final int DEFAULT_CAPACITY = 10;

	public ArrayList2() {
		elements = (E[]) new Object[DEFAULT_CAPACITY];
	}

	public ArrayList2(int size) {
		int capacity = (size > DEFAULT_CAPACITY) ? size : DEFAULT_CAPACITY;
		elements = (E[]) new Object[capacity];
	}

	private int index(int index) {
		index += first;
		if (index < 0)
			return index + elements.length;

		return (index > elements.length) ? index - elements.length : index;
	}

	private void ensureCapacity(int capcity) {
		int oldCapacity = elements.length;
		if (capcity < oldCapacity)
			return;

		int newCapacity = oldCapacity + (oldCapacity >> 1);
		E[] newElements = (E[]) new Object[newCapacity];

		for (int i = 0; i < size; i++) {

			newElements[i] = elements[index(i)];
		}
		first = 0;
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
			newElements[i] = elements[index(i)];
		}
		first = 0;
		elements = newElements;
		System.out.println("capacity:" + oldCapacity + " -> " + newCapacity);
	}

	@Override
	public E get(int index) {
		rangeCheck(index);
		return elements[index(index)];
	}

	@Override
	public E set(int index, E element) {
		rangeCheck(index);
		index = index(index);

		E oldElement = elements[index];
		elements[index] = element;
		return oldElement;
	}

	@Override
	public void add(int index, E element) {
		rangeCheckForAdd(index);
		ensureCapacity(size + 1);

		if (index < (size >> 1)) {// 插入點在前端->挪動前端
			for (int i = 0; i < index; i++)
				elements[index(i)] = elements[index(i + 1)];

			first--;
		} else {// 挪動後端
			for (int i = size; i > index; i--)
				elements[index(i)] = elements[index(i - 1)];
		}

		elements[index(index)] = element;
		size++;
	}

	@Override
	public E remove(int index) {
		rangeCheck(index);
		E old = elements[index(index)];

		if (index < (size >> 1)) {// 插入點在前端->挪動前端
			for (int i = index; i > 0; i--)
				elements[index(i)] = elements[index(i - 1)];

			elements[index(0)] = null;
			first = index(1);
		} else {// 挪動後端
			for (int i = index; i < size - 1; i++)
				elements[index(i)] = elements[index(i + 1)];

			elements[index(size - 1)] = null;
		}

		size--;
		trim();
		return old;
	}

	@Override
	public void clear() {
		for (int i = 0; i < size; i++)
			elements[index(i)] = null;

		size = 0;
		trim();
	}

	@Override
	public int indexOf(E element) {
		if (element == null) {
			for (int i = 0; i < size; i++) {
				if (element == elements[index(i)]) {
					return i;
				}
			}
		} else {
			for (int i = 0; i < size; i++) {
				if (element.equals(elements[index(i)])) {
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
			string.append(elements[index(i)]);
		}
		string.append("]");

		return string.toString();
	}
}

```
