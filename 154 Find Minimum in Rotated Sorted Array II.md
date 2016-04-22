# 154 Find Minimum in Rotated Sorted Array II

标签（空格分隔）： LeetCode Array BinarySearch

---

**Problem:**
>   Follow up for "Find Minimum in Rotated Sorted Array":
What if duplicates are allowed?
>
Would this affect the run-time complexity? How and why?
Suppose a sorted array is rotated at some pivot unknown to you beforehand.
>
(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).
>
Find the minimum element.
>
The array may contain duplicates.

**Analysis:**

 1. 给定一个有序的旋转数组，其中由重复的值，求其中的最小值。
 2. 和前一题一样，在判断中加一条相等则end值减1即可。

**Solution:**
```cpp
	int findMin(std::vector<int>& nums)
	{
		int start = 0;
		int end = nums.size( ) - 1;

		while (start < end)
		{
			int mid = start + (end - start) / 2;
			if (nums[mid] < nums[end])
				end = mid;
			else if (nums[mid] > nums[end])
				start = mid + 1;
			else
				end--;
		}

		return nums[start];
```
 
 
