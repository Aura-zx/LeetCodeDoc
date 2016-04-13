# 144 Binary Tree Preorder Traversal

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Given a binary tree, return the preorder traversal of its nodes' values.

 **Solution:**
 

 1. 将一个二叉树返回它的先序遍历。
 2. 参考reference，主要迭代版本的简洁性。

**Solution:**
```cpp
    // 递归版本
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
    
    // 迭代版本
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