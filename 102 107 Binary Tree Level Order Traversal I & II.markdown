# 102 107 Binary Tree Level Order Traversal I & II

标签（空格分隔）： LeetCode Tree BFS

---
**Problem:**
>   Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

>   For example:
Given binary tree {3,9,20,#,#,15,7},
>
     3
    / \
    9  20
    /  \
    15   7
>102 return its level order traversal as:
[
  [3],
  [9,20],
  [15,7]
]
>107 
[
  [15,7],
  [9,20],
  [3]
]

**Analysis:**

 1. 树的层序遍历，将每一层的节点存在vector里。
 2. 利用queue辅助BFS。
 3. 107和102不同的是将最后的结果翻转。

**Solution:**
```cpp
	std::vector<std::vector<int>> levelOrderBottom(TreeNode* root)
	{
		std::vector<std::vector<int>> res;
		if (!root)
			return res;
		std::queue<TreeNode*> tmp;
		tmp.push(root);
		tmp.push(NULL);					// divided level by NULL
		std::vector<int> level;
		while (tmp.empty( ) == false)
		{
			TreeNode*p = tmp.front( );
			tmp.pop( );
			if (p != NULL)
			{
				level.push_back(p->val);
				if (p->left)	tmp.push(p->left);
				if (p->right)	tmp.push(p->right);
			}
			else
			{
				res.push_back(level);
				if (tmp.empty( ) == false)		// This level is over
				{					
					tmp.push(NULL);
					level.clear( );
				}
			}
		}

		reverse(res.begin( ), res.end( ));	// for #107
		return res;
	}
```
