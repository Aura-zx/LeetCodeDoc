# 160 Intersection of two linked list

标签（空格分隔）： LeetCode Linked_List

---

**Problem:**
>   Write a program to find the node at which the intersection of two singly linked lists begins.


    For example, the following two linked lists:

    A:          a1 → a2
                       ↘
                         c1 → c2 → c3
                       ↗            
    B:     b1 → b2 → b3
    begin to intersect at node c1.


>   Notes:
    -If the two linked lists have no intersection at all, return null.
    -The linked lists must retain their original structure after the function returns.
    -You may assume there are no cycles anywhere in the entire linked structure.
    -Your code should preferably run in O(n) time and use only O(1) memory.
    
**Solution:**
```cpp
	ListNode *getIntersectionNode(ListNode *headA, ListNode *headB)
	{
		if (headA == NULL || headB == NULL)
			return NULL;						// check if there exists empty list

		ListNode *hA = headA;
		ListNode *hB = headB;
		int lengthA = 0;
		int lengthB = 0;

		// find length of two linked list
		while (headA != NULL)
		{
			headA = headA->next;
			lengthA++;
		}

		while (headB != NULL)
		{
			headB = headB->next;
			lengthB++;
		}
		
		// which list is longer , it go |M-N| steps
		int max = lengthA > lengthB ? 1 : 0;
		int diff = abs(lengthA - lengthB);
		if (max == 1)
		{
			while (diff != 0)
			{
				hA = hA->next;
				diff--;
			}
		}
		else
		{
			while (diff != 0)
			{
				hB = hB->next;
				diff--;
			}
		}

		// now they are the same length , compare one by one
		while (hA != NULL && hB != NULL)
		{
			if (hA == hB)
				return hA;
			else
			{
				hA = hA->next;
				hB = hB->next;
			}
		}
		return NULL;
	}
```
**Analysis:**

1. 题目求两个单链表相交的节点
2. 题目中的单链表没有圈
3. 求出2个链表的长度，将长的链表向后移动两个链表长度之差的步数
4. 此时两个链表长度一样，一一比较即可

**Reference:**
[找链表相交点的各种算法，包括有圈无圈，本次使用了算法I][1]


  [1]: http://richardhartersworld.com/cri/2008/linkedlist.html