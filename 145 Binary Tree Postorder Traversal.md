# 145 Binary Tree Postorder Traversal

标签（空格分隔）： LeetCode Tree

---

**Problem:**
>   Given a binary tree, return the postorder traversal of its nodes' values.

**Analysis:**

 1. 求一个二叉树的**后序遍历**。
 2. 见reference，注意迭代版本的简洁性。
 

**Solution:**
```cpp
	void postorder(TreeNode* node, std::vector<int>& ret)
	{
		if (node == NULL)
			return;
		else
		{
			postorder(node->left, ret);
			postorder(node->right, ret);
			ret.push_back(node->val);
		} 
	}
	std::vector<int> postorderTraversal(TreeNode* root)
	{
		std::vector<int> ret;
		if (root == NULL)
			return ret;
		else
			postorder(root, ret);

		return ret;
	}
	
	std::vector<int> postorderTraversal2(TreeNode* root)
	{
		std::vector<int> ret;
		std::stack<TreeNode*> s;
		TreeNode* peekNode = NULL;
		TreeNode* lastNodeVisited = NULL;
		if (root == NULL)
			return ret;

		while (root != NULL || !s.empty( ))
		{
			if (root != NULL)
			{
				s.push(root);
				root = root->left;
			}
			else
			{
				peekNode = s.top( );
				if (peekNode->right != NULL && lastNodeVisited != peekNode->right)
					root = peekNode->right;
				else
				{
					ret.push_back(peekNode->val);
					lastNodeVisited = s.top( );
					s.pop( );
				}
			}
		}

		return ret;
	}
```
**Reference:**
[二叉树的遍历][1]


  [1]: https://www.wikiwand.com/en/Tree_traversal