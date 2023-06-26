
```java
package code;

public class ListNode {
	public int value;
	public ListNode next;

	public ListNode() {
		next = null;
	}

	public ListNode(int value, ListNode next) {
		this.value = value;
		this.next = null;
	}

	@Override
	public String toString() {
		ListNode head = this;
		StringBuilder string = new StringBuilder();
		string.append("[");
		for (int i = 0; head != null; i++) {
			if (i != 0)
				string.append(", ");
			string.append(head.value);
			head = head.next;
		}
		string.append("]");

		return string.toString();
	}
}
```
