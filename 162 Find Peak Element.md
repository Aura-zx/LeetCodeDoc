# 162 Find Peak Element

标签（空格分隔）： LeetCode Array BinarySearch

---

**Problem:**
>   A peak element is an element that is greater than its neighbors.
Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.
The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.
You may imagine that num[-1] = num[n] = -∞.
For example, in array [1, 2, 3, 1], 3 is a peak element and your function should return the index number 2.

**Analysis:**

 1. 给一个数组，求它其中的peak element，就是比两边大的数字，头尾前后的数字默认为最小值，可能有许多符合的值，返回任意一个即可。
 2. 提示里要求为log复杂度，但是线性的就可以做，直接扫过去就好。

**Solution:**
```cpp
	int findPeakElement(std::vector<int>& nums)
	{
		if (nums.size( ) == 1)
			return 0;

		for (int i = 0; i < nums.size( ); i++)
		{
			if (i == 0)
			{
				if (nums[i] > nums[i + 1])
					return i;
			}

			if (i == nums.size( ) - 1)
			{
				if (nums[i] > nums[i - 1])
					return i;
			}

			if (nums[i] > nums[i - 1] && nums[i] > nums[i + 1])
				return i;
		}

		return -1;
	}
```
 
