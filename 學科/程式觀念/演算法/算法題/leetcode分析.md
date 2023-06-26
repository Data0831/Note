
# 876 鏈表中間節點

```java
public static ListNode middleNode(ListNode head) {
	ListNode slow = head, fast = head.next;
	while(true) {
		if(fast == null)	return slow;
		if(fast.next == null) 	return slow.next;
		fast = fast.next.next;
		slow = slow.next;
	}
}
```
