# 94 Binary Tree Inorder Traversal

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Given a binary tree, return the inorder traversal of its nodes' values.

**Analysis:**

 1. 求一个二叉树的**中序遍历**。
 2. 见reference，注意迭代版本的简洁性。

**Solution:**
```cpp
	void preorder(TreeNode* node, std::vector<int>& ret)
	{
		if (!node)
			return;
		ret.push_back(node->val);
		preorder(node->left, ret);
		preorder(node->right, ret);
	}

	std::vector<int> preorderTraversal(TreeNode* root)
	{
		std::vector<int> ret;

		if (!root)
			return ret;
		preorder( root, ret);

		return ret;
	}

	std::vector<int> preorderTraversal2(TreeNode* root)
	{
		std::stack<TreeNode*> s;
		std::vector<int> ret;
		while (!s.empty( ) || root != NULL)
		{
			if (root != NULL)
			{
				ret.push_back(root->val);
				if (root->right != NULL)
					s.push(root->right);
				root = root->left;
			}
			else
			{
				root = s.top( );
				s.pop( );
			}
		}

		return ret;
	}
```
 
 **Reference:**
 [二叉树的遍历][1]


  [1]: https://www.wikiwand.com/en/Tree_traversal