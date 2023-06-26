
```
public static ListNode nodeSet(int []arr) {
	ListNode node = new ListNode();
	ListNode now = node;

	for (int i = 0; i < arr.length; i++) {
		if(i==0) {
			node.value = arr[i];
			continue;
		}
		now.next = new ListNode(arr[i], null);
		now = now.next;
	}

	return node;
}
```
