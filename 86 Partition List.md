# 86 Partition List

标签（空格分隔）： LeetCode TwoPointers

---
**Problem:**
>   Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.
>
You should preserve the original relative order of the nodes in each of the two partitions.
>
For example,
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5.

**Analysis:**

 1. 给一个链表和一个值x，求把链表重新排列成所以小于x的数都在大于x的数的前面，同时他们的相对位置不变。
 2. 很简单的一道题，设两个list，一个记录小于x的值，一个记录大于x的值，然后将他们合并即可。

**Solution:**
```cpp
ListNode* partition(ListNode* head, int x)
	{
		ListNode* less = new ListNode(0);
		ListNode* grater = new ListNode(0);
		ListNode* node = head;

		ListNode* tl = less;
		ListNode* tg = grater;
		while (node != NULL)
		{
			if (node->val >= x)
			{
				tg->next = node;
				tg = tg->next;
			}
			
			if (node->val < x)
			{
				tl->next = node;
				tl = tl->next;
			}

			node = node->next;
		}

		tl->next = grater->next;
		tg->next = NULL;
		return less->next;
	}
```
 
