# 110 Balanced Binary Tree

标签（空格分隔）： LeetCode Tree DFS

---

**Problem:**
>   Given a binary tree, determine if it is height-balanced.
>
For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

**Analysis:**

 1. 判断一个二叉树树是否为平衡树，平衡树的定义是任何子树的高相差不超过1。
 2. 递归求每个子树的高，判断是否超过1，超过则返回`false`。
 3. 求树高单独写一个函数。

**Solution:**
```cpp
	bool isBalanced(TreeNode* root)
	{
		if (!root)
			return true;

		// subtree difference more than 1 ,return false
		if (abs(depth(root->left) - depth(root->right)) > 1)
			return false;

		bool left  = isBalanced(root->left);
		bool right = isBalanced(root->right);
		
		return left && right;
	}

	int depth(TreeNode* root)
	{
		if (root == NULL)
			return 0;

		return 1 + std::max(depth(root->left), depth(root->right));
	}
```

