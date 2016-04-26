# 74 Search a 2D Matrix

标签（空格分隔）： LeetCode BinarySearch Divide_and_Conquer

---

**Problem:**
>   Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:
>
Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.
For example,
>
Consider the following matrix:
[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
Given target = 3, return true.

**Analysis:**

 1. 给一个有序矩阵，每一行都是升序，下一行第一个数肯定比上一行最后一个数大，求找其中的特定元素。
 2. 直观的思路是先找特定的行，再在特定的行里面找那个数。
 3. 还可以把整个矩阵看成一个有序数组直接进行二分搜索，因为整个矩阵是严格有序的。
 4. 注意二分搜索的细节start <= end，每次赋值的时候对mid+1，mid-1操作。
 5. 卡在{{1}},0这个case，直接在一开始加了一个判断。

**Solution:**
```cpp
	bool searchMatrix(std::vector<std::vector<int>>& matrix, int target)
	{
		int m = matrix.size( );
		int n = matrix[0].size( );

		if (target < matrix[0][0])
			return false;
		int start = 0;
		int end = m - 1;

		while (start <= end)
		{
			int mid = start + (end - start) / 2;
			if (target == matrix[mid][0])
				return true;
			else if (target > matrix[mid][0])
				start = mid+1;
			else if (target < matrix[mid][0])
				end = mid-1;
		}

		int row = end;
		start = 0;
		end = n - 1;
		while (start <= end)
		{
			int mid = start + (end - start) / 2;
			if (target == matrix[row][mid])
				return true;
			else if (target > matrix[row][mid])
				start = mid+1;
			else if (target < matrix[row][mid])
				end = mid-1;
		}

			return false;
	}
```
 
