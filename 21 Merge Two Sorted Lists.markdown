# 21 Merge Two Sorted Lists

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.


**Analysis:**

 1. 将两个排好序的单链表合并。
 2. 以一个链表为基准，将第二个链表插入进来，注意头结点的使用。

**Solution:**
```cpp
	ListNode* mergeTwoLists(ListNode* l1, ListNode* l2)
	{
		ListNode* helper = new ListNode(0);
		ListNode* pre = helper;
		helper->next = l1;

		while (l1 && l2)
		{
			if (l1->val > l2->val)
			{
				ListNode* next = l2->next;
				l2->next = pre->next;
				pre->next = l2;
				l2 = next;
			}
			else
				l1 = l1->next;

			pre = pre->next;		// current pre->val is small than l1 and l2
		}

		if (l2 != NULL)
			pre->next = l2;			// l2 is not at end,but l1 is end,so link l2 is the rest part.

		return helper->next;
	}
```
 
