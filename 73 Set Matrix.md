# 73 Set Matrix

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given a m x n matrix, if an element is 0, set its entire row and column to 0. Do it in place.
>   follow up:
>   Did you use extra space?
A straight forward solution using O(mn) space is probably a bad idea.
A simple improvement uses O(m + n) space, but still not the best solution.
Could you devise a constant space solution?

**Analysis:**

 1. 给定一个矩阵，将其中某一行若有0则全部置0，某一列有0则全部置0；
 2. 首先遍历每个元素，将其中为0元素对应的行列值存起来；接着按照存储的行列值遍历整个矩阵得到最后的结果

**Solution:**
```cpp
	void setZeroes(std::vector<std::vector<int>>& matrix)
	{
		if (matrix.empty( ))
			return;

		int m = matrix.size( );
		int n = matrix[0].size( );

		std::set<int> row;
		std::set<int> col;
		for (int i = 0; i < m; i++)
		{
			for (int j = 0; j < n; j++)
			{
				if (matrix[i][j] == 0)
				{
					row.insert(i);
					col.insert(j);
					continue;
				}
			}
		}

		for (int i = 0; i < m; i++)
		{
			for (int j = 0; j < n; j++)
			{
				if (row.count(i))
					matrix[i][j] = 0;
				if (col.count(j))
					matrix[i][j] = 0;
			}
		}

		return;
	}
```
 
