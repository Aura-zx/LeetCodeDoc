# 48 Rotate Image

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   You are given an n x n 2D matrix representing an image.
>
Rotate the image by 90 degrees (clockwise).
>
Follow up:
Could you do this in-place?

**Analysis:**

 1. 给定一个n*n的矩阵，将这个矩阵向右旋转90度。
 2. 写出两个矩阵，找对应的关系，一圈一圈的移动元素。
 3. 90度的矩阵是原矩阵的转置矩阵每一行逆序的结果。

**Solution:**
```cpp
		int start = 0;
		int end = matrix.size( ) - 1;

		while (start < end)
		{
			for (int i = start; i < end; i++)
			{
				int offset = i - start;
				int tmp = matrix[start][i];
				matrix[start][i] = matrix[end - offset][start];
				matrix[end - offset][start] = matrix[end][end - offset];
				matrix[end][end - offset] = matrix[start+offset][end];
				matrix[start + offset][end] = tmp;
			}
			start++;
			end--;
		}
```
 
**Reference:**
[转置矩阵每行的逆序][1]


  [1]: http://blog.csdn.net/kenden23/article/details/17200067