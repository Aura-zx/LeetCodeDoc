# 213 House Robber II

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   After robbing those houses on that street, the thief has found himself a new place for his thievery so that he will not get too much attention. This time, all houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, the security system for these houses remain the same as for those in the previous street.
>
Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

**Analysis:**

 1. 给定一个循环数数组，求没有相邻的元素的序列的最大和。
 2. 和非循环数组的差别在于分两种情况，一种没有头元素，一种没有尾元素，分开处理即可。

**Solution:**
```cpp
	int rob(std::vector<int>& nums)
	{
		if (nums.empty())
			return 0;
		if (nums.size() == 1)
			return nums[0];
		if (nums.size() == 2)
			return std::max(nums[0], nums[1]);

		int size = nums.size();
		std::vector<int> ret1(size-1);
		ret1[0] = nums[0];
		ret1[1] = std::max(nums[0],nums[1]);
		for(int i = 2; i < ret1.size(); i++)
			ret1[i] = std::max(ret1[i-1], nums[i] + ret1[i-2]);

		std::vector<int> ret2(size-1);
		ret2[0] = nums[1];
		ret2[1] = std::max(nums[1],nums[2]);
		for(int i = 2; i < ret2.size(); i++)
			ret2[i] = std::max(ret2[i-1], nums[i+1]+ret2[i-2]);

		return std::max(ret1[size-2], ret2[size-2]);
	}
```
 
