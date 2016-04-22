# 153 Find Minimum in Rotated Sorted Array

标签（空格分隔）： LeetCode Array BinarySearch

---

**Problem:**
>   Suppose a sorted array is rotated at some pivot unknown to you beforehand.
>
(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).
>
Find the minimum element.

**Analysis:**

 1. 给一个经过旋转的有序数组，找出它的最小值。
 2. 即使是旋转矩阵依旧可用通过正常的二分法进行二分搜索。
 3. mid和end比较，若mid<end则表明最小的元素在前半部分。

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
			else
				start = mid + 1;
		}

		return nums[start];
	}
```
 
