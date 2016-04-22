# 81 Search in Rotated Sorted Array II

标签（空格分隔）： LeetCode Array BinarySearch

---

**Problem:**
>   Follow up for "Search in Rotated Sorted Array":
What if duplicates are allowed?
>
Would this affect the run-time complexity? How and why?
>
Write a function to determine if a given target is in the array.

**Analysis:**

 1. 给一个旋转后的有序数组，当它有重复的时候，找特定元素。
 2. 和前一题区别在于通过start和mid的比较不能判断数组的升序降序情况，有个很简单的办法，当他们相等的时候，将start向前进一步，接着如上一题算法计算即可。

**Solution:**
```cpp
		int start = 0;
		int end = nums.size( ) - 1;

		while (start <= end)
		{
			int mid = start + (end - start) / 2;
			if (nums[mid] == target)
				return true;
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
			else // start和mid相等时，start向前进一步即可
				start++;
		}

		return false;
```
  
