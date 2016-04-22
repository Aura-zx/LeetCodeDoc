# 63 Unique Paths II

标签（空格分隔）： LeetCode Array DP

---

 **Problem:**
 >  Follow up for "Unique Paths":
>
Now consider if some obstacles are added to the grids. How many unique paths would there be?
>
An obstacle and empty space is marked as 1 and 0 respectively in the grid.
>
For example,
There is one obstacle in the middle of a 3x3 grid as illustrated below.
>
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
The total number of unique paths is 2.

**Analysis:**

 1. 给一个矩阵，中间1表示不能通过，0表示可以通过，只能向右或向下，求从左上角到右下角的通路有多少条。
 2. 还是采用DP的办法，注意起点格子也会出现障碍的情况，这时可以直接输出0；
 3. 先用第一行数据初始化dp数组，注意数字1之后的格子都为0；
 4. 接下来和Unique Paths的算法类似，双重循环遍历，注意判断第一个格子是否为障碍。
 
**Solution:**
```cpp
int uniquePathsWithObstacles(std::vector<std::vector<int>>& obstacleGrid)
	{
		if (obstacleGrid.empty( ) || obstacleGrid[0][0] == 1)
			return 0;
		int m = obstacleGrid.size( );
		int n = obstacleGrid[0].size( );
		std::vector<int> dp(n, 0);

		for (int i = 0; i < n; i++)
		{
			if (obstacleGrid[0][i] == 0)
				dp[i] = 1;
			else
				break;
		}
		
		for (int i = 1; i < m; i++)
		{
			if (obstacleGrid[i][0] == 1)
				dp[0] = 0;
			for (int j = 1; j < n; j++)
			{
				if (obstacleGrid[i][j] == 1)
					dp[j] = 0;
				else
					dp[j] += dp[j - 1];
			}
		}
		
		return dp[n - 1];
```