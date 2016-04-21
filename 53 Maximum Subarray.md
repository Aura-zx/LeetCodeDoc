# 53 Maximum Subarray

标签（空格分隔）： LeetCode array

---

**Problem:**
>   Find the contiguous subarray within an array (containing at least one number) which has the largest sum.
>
For example, given the array [−2,1,−3,4,−1,2,1,−5,4],
the contiguous subarray [4,−1,2,1] has the largest sum = 6.

**Analysis:**

 1. 求一个数组最大子数组的和。
 2. 经典问题，见Reference和Solution。

**Solution:**
```cpp
	int maxSubarray(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;

		int sum_so_far = nums[0];
		int sum_end_here = nums[0];
		for (int i = 1; i < nums.size( ); i++)
		{
			sum_end_here = std::max(nums[i], sum_end_here + nums[i]);
			sum_so_far = std::max(sum_so_far, sum_end_here);
		}

		return sum_so_far;
	}
```

**Reference:**
[Maximum subarray problem][1]


  [1]: https://www.wikiwand.com/en/Maximum_subarray_problem