---
tags: 
aliase: 
created: 2023-02-01 09:46
modified: 星期三 1日 二月 2023 09:46:28
---

# Circle Linkedlist
***

```java
package isdouble;

public class CircleLinkedList<E> extends AbstractList<E> {
	private Node<E> first, last;

	private static class Node<E> {
		E element;
		Node<E> prev, next;

		public Node(E element, Node<E> prev, Node<E> next) {
			this.element = element;
			this.prev = prev;
			this.next = next;
		}

		@Override
		public String toString() {
			StringBuilder string = new StringBuilder();
			
			if (this.prev != null)
				string.append(this.prev.element);
			else
				string.append("null");
			
			string.append("-").append(this.element).append("-");
			
			if (this.next != null)
				string.append(this.next.element);
			else
				string.append("null");

			return string.toString();
		}

	}

	public Node<E> node(int index) {
		rangeCheck(index);
		Node<E> node;

		if (index > size / 2) {// 靠後
			node = last;
			for (int i = size - 1; i > index; i--)
				node = node.prev;
		} else {// 靠前
			node = first;
			for (int i = 0; i < index; i++)
				node = node.next;
		}

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
			
		if(size == 0) {
			first = new Node<>(element, null, null);
			last = first;
			first.next = first;
			first.prev = first;
		}else {
			Node<E> next = (index == size)? first: node(index);
			Node<E> prev = next.prev;// last
			prev.next = new Node<>(element, prev, next);
			next.prev = prev.next;
			
			if(index == size)
				last = prev.next;
			if(index == 0)
				first = prev.next;
		}

		size++;
	}

	@Override
	public E remove(int index) {
		rangeCheck(index);
		Node<E> node = node(index);

		if(size == 1) {
			first = last = null;
		}else { 
			Node<E> prev = node.prev, next = node.next;
			
			if (index == size - 1)
				last = last.prev;
			if (index == 0)
				first = first.next;

			if (prev != null)
				prev.next = next;
			if (next != null)
				next.prev = prev;
		}
			

		size--;
		return node.element;
	}

	@Override
	public void clear() {
		first = null;
		last = null;
		size = 0;
	}

	@Override
	public int indexOf(E element) {
		Node<E> node = first;
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
		Node<E> node = first;
		StringBuilder string = new StringBuilder();
		string.append("size: ").append(size).append(" [");

		for (int i = 0; i < size; i++) {
			if (i != 0)
				string.append(", ");
			string.append(node);
			node = node.next;
		}
		string.append("]");

		return string.toString();
	}
}
```
