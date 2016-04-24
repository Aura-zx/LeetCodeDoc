# 59 Spiral Matrix II

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given an integer n, generate a square matrix filled with elements from 1 to n2 in spiral order.
>
For example,
Given n = 3,
>
You should return the following matrix:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]

**Analysis:**

 1. 给一个数n，求1-n^2这些数螺旋填充到n*n的矩阵中。
 2. 因为长宽是一样的，所以这个题要简单一些，和上一题思路一样，模拟即可。


**Solution:**
```cpp
	std::vector<std::vector<int>> generateMatrix(int n)
	{
		std::vector<std::vector<int>> ret(n, std::vector<int>(n,0));

		int start = 0;
		int end = n - 1;
		int val = 1;

		while (start < end)
		{
			for (int j = start; j < end; j++)
				ret[start][j] = val++;
			for (int i = start; i < end; i++)
				ret[i][end] = val++;
			for (int j = end; j > start; j--)
				ret[end][j] = val++;
			for (int i = end; i > start; i--)
				ret[i][start] = val++;

			start++;
			end--;
		}

		if (start == end)
			ret[start][start] = val;

		return ret;
	}
```

