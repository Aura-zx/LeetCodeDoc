# 120 Triangle

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.
>
For example, given the following triangle
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

**Analysis:**

 1. 给一个三角形，求从顶端到底端的最小值，路径只能是下一行邻接的数字，即正下方和+1。
 2. 动态规划算法，从倒数第二行开始，s[i][j]表示从底端到这一行的最小值。
 3. 状态转移方程s[i][j] = min(s[i+1][j], s[i+1][j+1])+s[i][j]。

**Solution:**
```cpp
	int minimumTotal(std::vector<std::vector<int>>& triangle)
	{
		int size = triangle.size( )-1;

		for (int i = size-1; i >= 0; i--)
		{
			for (int j = 0; j <= i; ++j)
				triangle[i][j] += std::min(triangle[i + 1][j], triangle[i + 1][j + 1]);
		}

		return triangle[0][0];
	}
```
 
