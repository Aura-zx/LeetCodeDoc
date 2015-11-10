# 257 Binary Tree Node

标签（空格分隔）： Tree DFS

---

**Problem:**
>   Given a binary tree, return all root-to-leaf paths.
>
For example, given the following binary tree

**Analysis:**

 1. 题目要求一个二叉树的所有路径。
 2. DFS搜索即可。

**Solution:**
```cpp
std::vector<std::string> binaryTreePath(TreeNode* root)
	{
		std::vector<std::string> res;
		if (!root)
			return res;
		
		btdfs(root, std::to_string(root->val), res);

		return res;
	}

	void btdfs(TreeNode* root, std::string out, std::vector<std::string> &res)
	{
		if (!root->left && !root->right)
			res.push_back(out);
		if (root->left)
		{
			btdfs(root->left, out + "->" + std::to_string(root->left->val), res);
		}
		if (root->right)
		{
			btdfs(root->right, out + "->" + std::to_string(root->right->val), res);
		}
	}
```
 
