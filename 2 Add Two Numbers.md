# 2 Add Two Numbers

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.
>
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8

**Analysis:**

 1. 将两个链表加起来。
 2. 这里可以默认每一个node里的数字都是个位数，维护一个carry值分别加上两个链表节点的值，大于10的部分作为真实值放入结果节点，剩下的值参与下一次的计算。
 3. 注意while循环条件，l1 || l2 || carry 前两个条件可以解决两个链表长度不一样的情况，carry可以解决最后加和完毕多出来一位的1的情况。

**Solution:**
```cpp
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2)
	{
		ListNode* dummy = new ListNode(-1);
		ListNode* p = dummy;

		int carry = 0;
		while (l1 || l2 || carry)
		{
			if (l1 != nullptr)
			{
				carry += l1->val;
				l1 = l1->next;
			}
			if (l2 != nullptr)
			{
				carry += l2->val;
				l2 = l2->next;
			}

			p->next = new ListNode(carry % 10);
			carry /= 10;
			p = p->next;
		}

		return dummy->next;
	}
```
 
