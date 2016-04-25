# 147 Insertion Sort List

标签（空格分隔）： LeetCode Sort Linked_List

---

**Problem:**
>   Sort a linked list using insertion sort.

**Analysis:**

 1. 用插入排序给一个链表排序。
 2. 没什么好说的。

**Solution:**
```cpp
	ListNode* insertionSortList(ListNode* head)
	{
		ListNode* newhead = new ListNode(INT_MIN);
		while (head)
		{
			ListNode* cur = head;
			ListNode* p	  = newhead;
			head = head->next;
			while (p->next && p->next->val < cur->val)
				p = p->next;
			cur->next = p->next;
			p->next = cur;
		}

		head = newhead->next;
		delete newhead;
		return head;
	}
```
  
