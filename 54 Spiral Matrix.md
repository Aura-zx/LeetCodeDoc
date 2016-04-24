# 54 Spiral Matrix

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.
>
For example,
Given the following matrix:
>
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
You should return [1,2,3,6,9,8,7,4,5].

**Analysis:**

 1. 给一个m*n的矩阵，求它的螺旋顺序输出。
 2. 模拟螺旋路径，见代码。

**Solution:**
```cpp
std::vector<int> spiralOrder(std::vector<std::vector<int>>& matrix)
	{
		std::vector<int> ret;
		if (matrix.empty( ) || matrix.size( ) == 0)
			return ret;

		int m = matrix.size( );
		int n = matrix[0].size( );

		int x = 0;
		int y = 0;

		while (m > 0 && n > 0)
		{
			if (m == 1)
			{
				for (int i = 0; i < n; i++)
					ret.push_back(matrix[x][y++]);
				break;
			}
			else if (n == 1)
			{
				for (int i = 0; i < m; i++)
					ret.push_back(matrix[x++][y]);
				break;
			}

			// top -> right
			for (int i = 0; i < n - 1; i++)
				ret.push_back(matrix[x][y++]);
			// right -> down
			for (int i = 0; i < m - 1; i++)
				ret.push_back(matrix[x++][y]);
			// down -> left
			for (int i = 0; i < n - 1; i++)
				ret.push_back(matrix[x][y--]);
			// left -> top
			for (int i = 0; i < m - 1; i++)
				ret.push_back(matrix[x--][y]);

			x++;
			y++;
			m -= 2;
			n -= 2;
		}

		return ret;
```
 
