# 100 Same Tree

标签（空格分隔）： LeetCode Tree DFS

---

**Problem:**
>   Given two binary trees, write a function to check if they are equal or not.
    Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

**Analysis:**

 1. 题目要求判断两棵树是不是一样，一样的定义是每个节点对应都有且值一样。
 2. 递归搜索对比即可。
 3. 注意函数的返回值，返回左右子树的判断结果的`与`。

**Solution:**
```cpp
	bool isSameTree(TreeNode *p, TreeNode *q)
	{
		// root is empty
		if (p && q)
			return true;
		if (p && !q)
			return false;
		if (!p && q)
			return false;
		if (p->val != q->val)
			return false;
		
		bool left = isSameTree(p->left, q->left);
		bool right = isSameTree(p->right, q->right);

		return left & right;
	}
```