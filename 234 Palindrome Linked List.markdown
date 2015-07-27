# 234 Palindrome Linked List

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Given a singly linked list, determine if it is a palindrome.

**Solution:**
```cpp
bool isPalindrome(ListNode *head)
	{
		if (!head)
			return true;

		// get mid Node
		ListNode *slow = head;
		ListNode *fast = head;
		while (fast->next != NULL && fast->next->next != NULL)
		{
			slow = slow->next;
			fast = fast->next->next;
		}

		// reverse last half list
		ListNode *mid = slow->next;
		ListNode *tmp;
		ListNode *pre = NULL;
		while (mid != NULL)
		{
			tmp = mid->next;
			mid->next = pre;
			pre = mid;
			mid = tmp;
		}

		// compare with reversed list and first half list
		while (head != NULL && pre != NULL)
		{
			if (head->val == pre->val)
			{
				head = head->next;
				pre = pre->next;
			}
			else
				return false;
		}
		return true;
	}
```

**Analysis:**

 1. 题目要求判断一个单链表是否为回文
 2. 思路是找到链表的前后部分，将后半部分反转，再和前半部分一一比较
 3. 找前后部分可以通过遍历链表长度**或者**快慢链表
 4. 图中代码反转之后的链表形式是中间节点和后半部分链表指向同一个`NULL`节点

