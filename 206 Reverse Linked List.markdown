# 206 Reverse Linked List

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Reverse a singly linked list.

**Solution:**
```cpp
	ListNode* reverseList(ListNode* head)
	{
		ListNode *pre = NULL;
		while (head != NULL)
		{
			ListNode *tmp = head->next;
			head->next = pre;
			pre = head;
			head = tmp;
		}
		return pre;
	}
```
**Analysis:**

 1. 翻转单链表
 2. 1-2-3
    第一次: pre = 1-null
    第二次: pre = 2-1-null
    第三次: pre = 3-2-1-null
