# 64 Minimum Path Sum

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

**Analysis:**

 1. 给一个m*n的矩阵，矩阵中的数字代表从这一格通过的代价，求从左上角到右下角最小代价。
 2. 简单的DP，ret[i][j] = min(ret[i-1][j], ret[i][j-1])+gird[i][j]

**Solution:**
```cpp
	int minPathSum(std::vector<std::vector<int>>& grid)
	{
		int m = grid.size( );
		int n = grid[0].size( );
		std::vector<std::vector<int>> ret(m, std::vector<int>(n, 0));
		ret[0][0] = grid[0][0];

		for (int i = 1; i < n; i++)
		{
			ret[0][i] = ret[0][i - 1] + grid[0][i];
		}
		for (int i = 1; i < m; i++)
		{
			ret[i][0] = ret[i - 1][0] + grid[i][0];
		}

		for (int i = 1; i < m; i++)
		{
			for (int j = 1; j < n; j++)
			{
				ret[i][j] = std::min(ret[i - 1][j], ret[i][j - 1])+grid[i][j];
			}
		}

		return ret[m-1][n-1];
	}
```
  
