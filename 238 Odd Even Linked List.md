# 238 Odd Even Linked List

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.
>
You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.
>
Example:
Given 1->2->3->4->5->NULL,
return 1->3->5->2->4->NULL.

**Analysis:**

 1. 将一个链表原地重新排列成奇数项在前，偶数项在后的新链表。
 2. 根据题意直接插入链表即可，设odd，even表示当前的插入位置，oddhead，evenhead表示两个子链表的头，最后将odd->next = evenhead即可。

**Solution:**
```cpp
	ListNode* oddEvenList(ListNode* head)
	{
		if (head != NULL)
			return head;

		ListNode* odd = head;
		ListNode* oddhead = odd;

		ListNode* even = head->next;
		ListNode* evenhead = even;
		
		while (even != NULL && even->next != NULL)
		{
			odd->next = even->next;
			odd = odd->next;
			even->next = odd->next;
			even = even->next;
		}

		odd->next = evenhead;
		return oddhead;
	}
```
 
