# 33 Search in Rotated Sorted Array

标签（空格分隔）： LeetCode Array BinarySearch

---
**Problem:**
>   
Suppose a sorted array is rotated at some pivot unknown to you beforehand.
>
(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).
>
You are given a target value to search. If found in the array return its index, otherwise return -1.
>
You may assume no duplicate exists in the array.

**Analysis:**

 1. 给一个旋转后的有序数组，找出其中的特定的元素。
 2. 正常二分法判断，start和mid的关系，注意start>mid这种情况，若target大于start或者小于mid则表示start在后半段，其他情况在前半段。

**Solution:**
```cpp
	int search(std::vector<int>& nums, int target)
	{
		int start = 0;
		int end = nums.size( ) - 1;

		while (start <= end)
		{
			int mid = start + (end - start) / 2;
			if (nums[mid] == target)
				return mid;
			if (nums[start] < nums[mid])
			{
				if (target >= nums[start] && target <= nums[mid])
					end = mid - 1;
				else
					start = mid + 1;
			}
			else if (nums[start] > nums[mid])
			{
				if (target >= nums[start] || target <= nums[mid])
					end = mid - 1;
				else
					start = mid + 1;
			}
			else // start 和 mid相等的情况
				start++;
		}

		return -1;
	}
```
 
