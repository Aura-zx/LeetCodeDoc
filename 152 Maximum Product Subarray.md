# 152 Maximum Product Subarray

标签（空格分隔）： LeetCode Array DP

---

**Problem:**
>   Find the contiguous subarray within an array (containing at least one number) which has the largest product.
>
For example, given the array [2,3,-2,4],
the contiguous subarray [2,3] has the largest product = 6.

**Analysis:**

 1. 求一个数组中子数组的最大乘积。
 2. 在常规的维护最大值的过程中，因为负数的存在维护一个最小值，取这两个值中间的最大值。

**Solution:**
```cpp
	int maxProduct(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;

		int maxlocal = nums[0];
		int minlocal = nums[0];
		int global = nums[0];

		for (int i = 1; i < nums.size( ); i++)
		{
			int maxcopy = maxlocal;
			maxlocal = std::max(std::max(maxlocal*nums[i], nums[i]), nums[i] * minlocal);
			minlocal = std::min(std::min(maxcopy*nums[i], nums[i]), nums[i] * minlocal);
			global = std::max(maxlocal, global);
		}

		return global;
	}
```
 
