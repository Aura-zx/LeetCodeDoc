# 101 Symmetric Tree

标签（空格分隔）： LeetCode Tree DFS

---

**Problem:**
>   Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

>   For example, this binary tree is symmetric:

       1
      / \
     2   2
    / \ / \
    3  4 4  3
    But the following is not:
     1
    / \
    2   2
    \   \
    3    3

**Analysis:**

 1. 判断一个数是否为镜像树。
 2. 需要判断左子树的左子树和右子树的右子树是否一样，左子树的右子树和右子树的左子树是否一样。
 3. 需要辅助函数`isSymmetric(root1, root2)`。

**Solution:**
```cpp
	bool isSymmetric(TreeNode* root)
	{
		return isSymmetric(root, root);
	}

	bool isSymmetric(TreeNode* root1, TreeNode* root2)
	{
		if (root1 == NULL && root2 == NULL)
			return true;

		if (root1 && root2 && root1->val == root2->val)
			return isSymmetric(root1->left, root2->right) &&
			       isSymmetric(root1->right, root2->left);

		return false;
	}
```

