---
tags: 
aliase: 
created: 2023-02-01 09:29
modified: 星期三 1日 二月 2023 09:29:29
---

# Single Linkedlist
***
>Single Linkedlist (sudo header)

- 虛擬頭節點
```java
package single;

import isdouble.AbstractList;

public class SingleLinkedList2<E> extends AbstractList<E> {
	private Node<E> first;
	
	public SingleLinkedList2() {
		first = new Node<>(null, null);
	}
	
	private static class Node<E> {
		E element;
		Node<E> next;

		public Node(E element, Node<E> next) {
			this.element = element;
			this.next = next;
		}
	}
	
	public Node<E> node(int index) {
		if(index != -1)	rangeCheck(index);
		Node<E> node = first;
		for (int i = 0; i <= index; i++)
			node = node.next;

		return node;
	}

	@Override
	public E get(int index) {
		return node(index).element;
	}

	@Override
	public E set(int index, E element) {
		Node<E> node = node(index);
		E old = node.element;
		node.element = element;
		return old;
	}

	@Override
	public void add(int index, E element) {
		rangeCheckForAdd(index);
		Node<E> prev = node(index - 1);
		prev.next = new Node<>(element, prev.next);
		size++;
	}

	@Override
	public E remove(int index) {
		rangeCheck(index);
		
		Node<E> prev = node(index - 1);
		Node<E> node = prev.next;
		prev.next = node.next;// prev.next = prev.next.next
		
		size--;
		return node.element;
	}

	@Override
	public void clear() {
		first.next = null;
		size = 0;
	}

	@Override
	public int indexOf(E element) {
		Node<E> node = first.next;
		if (element == null) {
			for (int i = 0; i < size; i++) {
				if (element == node.element)
					return i;
				node = node.next;
			}
		} else {
			for (int i = 0; i < size; i++) {
				if (element.equals(node.element))
					return i;
				node = node.next;
			}
		}

		return ELEMENT_NOT_FOUND;
	}

	public String toString() {
		Node<E> node = first.next;
		StringBuilder string = new StringBuilder();
		string.append("size: ").append(size).append(" [");
		
		for (int i = 0; i < size; i++) {
			if (i != 0)
				string.append(", ");
			string.append(node.element);
			node = node.next;
		}
		string.append("]");

		return string.toString();
	}
}
```
