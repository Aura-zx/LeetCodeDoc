# 96 Unique Binary Search Trees

标签（空格分隔）： LeetCode DP

---
**Problem:**
>   Given n, how many structurally unique BST's (binary search trees) that store values 1...n?
>
For example,
Given n = 3, there are a total of 5 unique BST's.

**Analysis:**

 1. 给定数字n，求1-n这些数能组成多少个唯一的搜索二叉树。
 2. 提示里提到了动态规划，设k为根，则可以组成的UBST个数为dp[1--k-1]*dp[k+1--n]，即左子树的个数乘以右子树的个数。
 3. 其中不同元素组成的子树个数是唯一的，设dp[i]为**i个数字**可以组成的唯一BST的个数，dp[i] = dp[j]*dp[i-j-1]，其中j属于[0,i-1]。

**Solution:**
```cpp
	int numTrees(int n)
	{
		std::vector<int> dp(n + 1, 0);
		dp[0] = 1;
		dp[1] = 1;
		
		for (int i = 2; i <= n; i++)
		{
			for (int j = 0; j < i; j++)
			{
				dp[i] += dp[j] * dp[i - j - 1];
			}
		}

		return dp[n];
	}
```
 
