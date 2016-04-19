# 142 Linked List Cycle

标签（空格分隔）： LeetCode Linked_List TwoPointers

---

**Problem:**
>   Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

**Analysis:**

 1. 判断一个单链表是否有环，如果有则返回环的入口节点，无则返回NULL。
 2. 当他们相遇时，将任意指针从head开始遍历，两个指针都step by step，再次相遇的节点即为入口节点。
 3. 分析见Reference

**Solution:**
```cpp
	ListNode *detectCycle(ListNode* head)
	{
		ListNode* first = head;
		ListNode* second = head;

		while (first != NULL && second != NULL)
		{
			first = first->next;
			second = second->next;
			if (second != NULL)
				second = second->next;
			if (first == second)
				break;
		}

		if (second == NULL)
			return NULL;

		first = head;
		while (first != second)
		{
			first = first->next;
			second = second->next;
		}

		return second;
	}
```




**Reference:**
[英文][1]
[中文][2]


  [1]: https://leetcode.com/discuss/16567/concise-solution-using-with-detailed-alogrithm-description
  [2]: http://www.qiujiawei.com/leetcode-problem-142/