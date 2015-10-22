# 26 Remove Duplicates from Sorted Array

标签（空格分隔）： LeetCode Array TwoPointers

---

**Problem:**
>   Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.

>   Do not allocate extra space for another array, you must do this in place with constant memory.
>
For example,
Given input array nums = [1,1,2],
>
Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.


**Analysis:**

 1. 和之前去除特定值的题类似，但需要动态更新val值
 2. 当值不一样时复制进vector，同时更新val。

**Solution:**
```cpp
int removeDuplicates(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;

		int  val    = nums[0];
		bool dup    = false;
		int  begin  = 1;
		for (size_t i = 1; i < nums.size( ); i++)
		{
			if (nums[i] != val)
			{
				nums[begin++] = nums[i];
				val = nums[i];
			}
		}

		return begin;
	}
```
  
