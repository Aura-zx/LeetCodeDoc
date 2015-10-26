# 19 Remove Nth Node from End of List

标签（空格分隔）： LeetCode TwoPointers

---

**Problem:**
>   Given a linked list, remove the n-th node from the end of list and return its head.
>
For example,
>
    Given linked list: 1->2->3->4->5, and n = 2.
    After removing the second node from the end, the linked list becomes 1->2->3->5.

**Analysis:**

 1. 问题求删除链表倒数第n个节点。
 2. 第一步想到的是遍历链表得到长度，最后再删除特定节点。
 3. one pass的办法是设置两个指针，第二个指针先移动n步，接着两个指针一步步的移动。
    当第二个指针为`NULL`时，第一个指针为需要删除的节点。

**Solution:**
```cpp
	ListNode* removeNthElementFromEnd(ListNode *head, int n)
	{
		ListNode* dummy = new ListNode(0);
		dummy->next = head;
		ListNode *pre = dummy;
		ListNode *cur = dummy->next;
		ListNode *end = dummy->next;
		while (n > 0)
		{
			end = end->next;
			n--;
		}
		if (end == NULL)
			return cur->next;

		while (end != NULL)
		{
			end = end->next;
			pre = pre->next;
			cur = cur->next;
		}

		ListNode *tmp = cur->next;
		pre->next = tmp;
		cur = tmp;

		return dummy->next;
	}
```

