# 111 Minimum Depth of Binary Tree

标签（空格分隔）： LeetCode Tree DFS BFS

---

**Problem:**
>   Given a binary tree, find its minimum depth.

>The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Analysis:**

 1. 题目求一个树的最短深度。
 2. 分别求左右子树的最小深度，分情况判断。
 3. 当左右都为0时，返回1；当左右子树有一个0时，返回最大的深度；都不为0时，返回二者中最小的。

**Solution:**
```cpp
	int minDepth(TreeNode* root)
	{
		if (!root)
			return 0;

		int left = minDepth(root->left);
		int right = minDepth(root->right);
		
		if (left != 0 && right != 0)
			return 1+std::min(left, right);
		else if (left == 0 && right == 0)
			return 1;
		else
			return 1+std::max(left, right);
	}
```

