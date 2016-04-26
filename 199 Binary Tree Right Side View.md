# 199 Binary Tree Right Side View

标签（空格分隔）： LeetCode Tree BFS

---

**Problem:**
>   Given a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.
>
For example:
Given the following binary tree,
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---
You should return [1, 3, 4].

**Analysis:**

 1. 求一个树从右边看是那些数字。
 2. 层序遍历，将每一层的结果存下来，只取最后一个。
 3. 另一种思路和层序遍历很像，维护一个maxlevel，当maxlevel小于level时，获取这个值。这个思路的核心是优先遍历右子树。见Reference。

**Solution:**
```cpp
int height(TreeNode* root)
	{
		if (!root)
			return 0;

		int l = height(root->left);
		int r = height(root->right);

		return std::max(l, r) + 1;
	}

	void levelOrderTraversal(TreeNode* root, int level, std::vector<int>& ret)
	{
		if (!root)
			return;

		if (level == 1)
			ret.push_back(root->val);
		else if (level > 1)
		{
			levelOrderTraversal(root->left, level - 1, ret);
			levelOrderTraversal(root->right, level - 1, ret);
		}
	}

	std::vector<int> rightSideView(TreeNode* root)
	{
		int h = height(root);

		std::vector<int> ret;
		for (int i = 1; i <= h; i++)
		{
			std::vector<int> tmp;
			levelOrderTraversal(root, i, tmp);
			ret.push_back(tmp[tmp.size()-1]);
		}
		
		return ret;
	}
```

**Reference:**
[树的右视图][1]


  [1]: http://www.geeksforgeeks.org/print-right-view-binary-tree-2/