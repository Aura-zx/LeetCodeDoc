# 11 Container With Most Water

标签（空格分隔）： LeetCode Array TwoPointers

---

**Problem:**
>   Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Analysis:**

 1. 给几根垂直的柱子，求任何两个柱子之间能存储的最大水量是多少。
 2. 从最左边和最右边的柱子开始向中间遍历，核心思想是此时的间隔最大，若是之后的柱子不能比这两根柱子高，则必然不能比它存储的水量多，相当于是控制了一个变量来剔除一部分不符合要求的情况。
 3. 决定装水多少的是最短的那根柱子，所以每次移动最短的柱子。

**Solution:**
```cpp
		if (height.empty( ))
			return 0;

		int maxarea = 0;
		int left = 0;
		int right = height.size( ) - 1;
		while (left < right)
		{
			int curarea = std::min(height[left], height[right]) * (right - left);
			maxarea = std::max(curarea, maxarea);
			if (height[left] < height[right])
				left++;
			else if (height[left] > height[right])
				right--;
			else
			{
				left++;
				right--;
			}
		}

		return maxarea;
```
 
**Reference:**
[图解][1]


  [1]: http://www.cnblogs.com/lautsie/p/3219461.html