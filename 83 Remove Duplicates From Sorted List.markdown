# 83 Remove Duplicates From Sorted List

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Given a sorted linked list, delete all duplicates such that each element appear only once.
    For example,
    Given 1->1->2, return 1->2.
    Given 1->1->2->3->3, return 1->2->3.
    
**Analysis:**

 1. 去除有序链表中重复的元素

**Solution:**
```cpp
ListNode *deleteDuplicates(ListNode* head)
	{
		if (!head)
			return head;

		ListNode *cur = head;

		while (cur->next)
		{
			if (cur->val == cur->next->val)
				cur->next = cur->next->next;
			else
				cur = cur->next;
		}

		return head;
	}
```

