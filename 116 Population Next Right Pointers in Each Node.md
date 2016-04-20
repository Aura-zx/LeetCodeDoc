# 116 Population Next Right Pointers in Each Node

标签（空格分隔）： LeetCode Tree DFS

---

**Problem:**
>   Given a binary tree

    struct TreeLinkNode {
      TreeLinkNode *left;
      TreeLinkNode *right;
      TreeLinkNode *next;
    }

>   
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.
>
Initially, all next pointers are set to NULL.

**Analysis:**

 1. 给一个二叉链接树，要求把相同层数的节点链接起来。
 2. 见代码。

**Solution:**
```cpp
void connect(TreeLinkNode *root)
	{
		if (root == NULL)
			return;

		TreeLinkNode* lastHead = root;		// 上一层的头
		TreeLinkNode* lastCurrent = NULL;	// 上一层的节点
		TreeLinkNode* curHead = NULL;		// 当前的头
		TreeLinkNode* cur = NULL;			// 当前的节点

		// lastCurrent一层层的遍历整个树
		while (lastHead != NULL)
		{
			lastCurrent = lastHead;

			while (lastCurrent != NULL)
			{
				if (curHead == NULL)
				{
					curHead = lastCurrent->left;
					cur = lastCurrent->left;
				}
				else
				{
					cur->next = lastCurrent->left;
					cur = cur->next;
				}

				if (curHead != NULL)
				{
					cur->next = lastCurrent->right;
					cur = cur->next;
				}

				lastCurrent = lastCurrent->next;
			}


			lastHead = curHead;
			curHead = NULL;
		}
	}
```
 
**Reference:**
[二叉链接树][1]


  [1]: http://www.programcreek.com/2014/05/leetcode-populating-next-right-pointers-in-each-node-java/