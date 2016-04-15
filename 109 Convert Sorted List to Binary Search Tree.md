# 109 Convert Sorted List to Binary Search Tree

标签（空格分隔）： LeetCode Tree

---
**Problem:**
>   Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.

**Analysis:**

 1. 将一个有序单链表转换成平衡二叉树。
 2. 可以采取和数组相同的办法做，稍微麻烦一点点，需要遍历链表找出中间节点。
 3. 还可以采取自下而上的办法构建BST，注意参数是head的地址，见Reference。

**Solution:**
```cpp
	TreeNode* buildTree(ListNode* node, int count)
	{
		if (count <= 0)
			return NULL;
		int rootindex = count / 2;
		ListNode* rootnode = node;
		for (int i = 0; i < rootindex; i++)
		{
			rootnode = rootnode->next;
		}
		TreeNode* root = new TreeNode(rootnode->val);
		root->left = buildTree(node, rootindex);
		root->right = buildTree(rootnode->next, count - rootindex - 1);

		return root;
	}

	TreeNode* buildTree2(ListNode** head, int count)
	{
		if (count <= 0)
			return NULL;

		TreeNode* left = buildTree2(head, count / 2);

		TreeNode* root = new TreeNode((*head)->val);
		root->left = left;

		*head = (*head)->next;
		root->right = buildTree2(head, count - count / 2 - 1);

		return root;
	}

	TreeNode* sortedListToBST(ListNode* head)
	{
		int count = 0;
		ListNode* node = head;
		while (node != NULL)
		{
			++count;
			node = node->next;
		}
		return buildTree(head, count);
	}
```
 
**Reference:**
[单链表构建平衡二叉树][1]


  [1]: http://www.geeksforgeeks.org/sorted-linked-list-to-balanced-bst/