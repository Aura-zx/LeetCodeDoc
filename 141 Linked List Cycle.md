# 141 Linked List Cycle

标签（空格分隔）： LeetCode Linked_List TwoPointers

---

**Problem:**
>   Given a linked list, determine if it has a cycle in it.

**Analysis:**

 1. 找出一个单链表是否有环。
 2. 典型的快慢指针问题，一个指针一次走一步，另一个一次走两步，当他们相等且不为NULL的时候则为有环。

**Solution:**
```cpp
bool hasCycle(ListNode *head)
	{
		if (!head)
			return false;

		ListNode* slow = head;
		ListNode* fast = head;
		while (fast && fast->next)
		{
			slow = slow->next;
			fast = fast->next->next;
			if (slow == fast)
				return true;
		}

		return false;
```
 
