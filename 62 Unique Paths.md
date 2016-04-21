# 62 Unique Paths

标签（空格分隔）： LeetCode Array DP

---

**Problem:**
>   A robot is located at the top-left corner of a m x n grid (marked 'Start' in the diagram below).
>
The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).
>
How many possible unique paths are there?

**Analysis:**

 1. m*n的矩阵，从左上角走到右下角共有多少条路，只能向右或向下走。
 2. Climbing Stairs的二维版，DP思路DP[i][j] = DP[i-1][j]+DP[i][j-1]
 3. 小技巧是可以用滚动数组优化space，在二维数组里每一次都只用了某一行的信息，下次就不再用了，见代码
 4. 二维版的数组见reference

**Solution:**
```cpp
	int uniquePaths(int m, int n)
	{
		if (m < 1 || n < 1)
			return 0;

		std::vector<int> dp(n, 1);
		for (int i = 1; i < m; i++)
			for (int j = 1; j < n; j++)
				dp[j] += dp[j - 1];

		return dp[n - 1];
	}
```
  
  **Reference:**
  [二维数组的构造过程][1]


  [1]: http://yucoding.blogspot.com/2013/04/leetcode-question-116-unique-path-i.html