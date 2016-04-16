# 337 House Robber III

标签（空格分隔）： LeetCode DP

---
**Problem:**
>   The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.
>
Determine the maximum amount of money the thief can rob tonight without alerting the police.

**Analysis:**

 1. 给定一个树，求不相邻层数的序列和的最大值。
 2. 树形DP，返回根节点在偷与不偷中的最大值即可。
 3. rob_root = max(rob_L + rob_R , no_rob_L + no_nob_R + root.val)
    no_rob_root = rob_L + rob_R



**Solution:**
```cpp
	std::pair<int, int> dfs(TreeNode* root)
	{
		std::pair<int, int> dp = std::make_pair(0, 0);
		if (root)
		{
			std::pair<int, int> dp_l = dfs(root->left);
			std::pair<int, int> dp_r = dfs(root->right);
			dp.second = dp_l.first + dp_r.first;
			dp.first = std::max(dp.second, dp_l.second + dp_r.second + root->val);
		}

		return dp;
	}

	int rob(TreeNode* root)
	{
		return dfs(root).first;
	}
```