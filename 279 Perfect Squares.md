# 279 Perfect Squares

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.
>
For example, given n = 12, return 3 because 12 = 4 + 4 + 4; given n = 13, return 2 because 13 = 4 + 9.


**Analysis:**

 1. 给一个正整数n，求能和为它的最小的完全平方数的个数。
 2. DP解决的思路，将DP[i]设置为和为i的完全平方数的个数，DP[i+j*j]=min(DP[i]+1, DP[i+j*j]) 。
 3. DP[i]+1,表示个数+1，同时也表示具体的完全平方数“1”。

**Solution:**
```cpp
	int numSquares(int n)
	{
		std::vector<int> dp(n+1, INT_MAX);

		for (int i = 0; i*i <= n; i++)
		{
			dp[i*i] = 1;
		}

		for (int i = 1; i <= n; i++)
		{
			for (int j = 1; i + j*j <= n; j++)
				dp[i + j*j] = std::min(dp[i] + 1, dp[i + j*j]);
		}

		return dp[n];
	}
```