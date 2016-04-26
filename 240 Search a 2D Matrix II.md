# 240 Search a 2D Matrix II

标签（空格分隔）： LeetCode BinarySearch Divide_and_Conquer

---

**Problem:**
>   Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
>
Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
For example,
>
Consider the following matrix:
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
Given target = 5, return true.
Given target = 20, return false.

**Analysis:**

 1. 给一个有序矩阵，每行从左到右是升序，每列从上到下是升序，求矩阵里有没有特定的数字。
 2. 从左下角开始搜索，如果小于当前元素就向上搜索，大于就向右搜索。
 3. 注意细节比如这里要使用前置的连续算符，还有if条件的写法。

**Solution:**
```cpp
	bool searchMatrix(std::vector<std::vector<int>>& matrix, int target)
	{
		int m = matrix.size( )-1;
		int n = matrix[0].size( )-1;

		int i = m;
		int j = 0;
		int cur = matrix[i][j];
		while (1)
		{
			if (target > cur && j != n)
				cur = matrix[i][++j];
			else if (target < cur && i != 0)
				cur = matrix[--i][j];
			else if (cur == target)
				return true;
			else
				return false;
		}
	}
```
  
