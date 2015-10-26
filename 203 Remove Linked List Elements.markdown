# 203 Remove Linked List Elements

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Remove all elements from a linked list of integers that have value val.
>
Example
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5

**Analysis:**

 1. 去除链表中的和目标元素重复的节点。
 2. 给链表加上dummy节点，处理删除头结点的情况。
 3. 维护一个pre节点，遍历节点即可。

**Solution:**
```cpp
	ListNode* removeElements(ListNode* head, int val)
	{
		ListNode *dummy = new ListNode(0);
		dummy->next = head;
		ListNode *pre = dummy;
		ListNode *cur = dummy->next;

		while (cur != NULL)
		{
			if (cur->val == val)
			{
				ListNode* tmp = cur->next;
				pre->next = tmp;
				cur = tmp;
			}
			else
			{
				pre = pre->next;
				cur = cur->next;
			}
		}

		return dummy->next;
	}
```

