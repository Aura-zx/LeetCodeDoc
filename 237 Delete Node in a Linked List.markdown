# 237 Delete Node in a Linked List

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

>   Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

**Solution:**
```cpp
	void deleteNode(ListNode* node)
	{
		ListNode *tmp = node->next;
		node->val = tmp->val;
		node->next = tmp->next;
	}
```

**Analysis:**

 1. 题目的意思是删除一个单链表的节点，函数参数很有意思，只给了要删除的节点。
 2. 按照传统的办法是用前面的节点`next`域指向要删除节点的`next`域，但访问不了前面的节点。
 3. 把后面节点的值和`next`域赋值给当前节点，则在实际上完成了对当前节点的删除，它的`val`值和`next`域都被删除。

