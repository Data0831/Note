---
tags:
aliase: 
created: 2023-02-01 09:42
modified: 星期三 1日 二月 2023 09:42:48
---

# Single CircleLinkedlist
***

```java
package single;

import isdouble.AbstractList;

public class SingleCircleLinkedList<E> extends AbstractList<E> {
	private Node<E> first;

	private static class Node<E> {
		E element;
		Node<E> next;

		public Node(E element, Node<E> next) {
			this.element = element;
			this.next = next;
		}

		@Override
		public String toString() {
			StringBuilder string = new StringBuilder();
			
			string.append(this.element).append("-");
			if(this.next != null)
				string.append(this.next.element);
			else 
				string.append("null");
			
			return string.toString();
		}
		
		
	}

	public Node<E> node(int index) {
		rangeCheck(index);
		Node<E> node = first;
		for (int i = 0; i < index; i++)
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
		if (index == 0) {
			first = new Node<>(element, first);//first 增加長度1
			Node<E> last = (size==0)? first: node(size-1).next;//.next彌補增加的長度
			last.next = first;
		}
		else {
			Node<E> prev = node(index - 1);
			prev.next = new Node<>(element, prev.next);
		}

		size++;
	}

	@Override
	public E remove(int index) {
		rangeCheck(index);
		Node<E> node = first;
		
		if(size == 1)
			first = null;
		else {
			if (index == 0) {
				Node<E> last = node(size-1);
				first = first.next;
				last.next = first;
			}
			else {
				Node<E> prev = node(index - 1);
				node = prev.next;
				prev.next = node.next;// prev.next = prev.next.next
			}
		}
		
		

		size--;
		return node.element;
	}

	@Override
	public void clear() {
		first = null;
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
			string.append(node.element);
			node = node.next;
		}
		string.append("]");

		return string.toString();
	}
}
```
