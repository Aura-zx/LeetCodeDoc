# 198 House Robber

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.
>
Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.


**Analysis:**

 1. 题目求一组数中加起来最大的一个序列，且这些数不能相邻。
 2. 用DP来做，设m[size]为我们求的数组，n[size]为给的数组。
 3. m[i] = max(m[i-1], n[i]+m[i-2]), m[0] = n[0], m[1] = max(n[0], n[1])

**Solution:**
```cpp
	int rob(std::vector<int>& nums)
	{
		if (nums.empty( ) == true)
			return 0;
		if (nums.size( ) == 1)
			return nums[0];
		if (nums.size( ) == 2)
			return std::max(nums[0], nums[1]);

		std::vector<int> res(nums.size( ));
		res[0] = nums[0];
		res[1] = std::max(nums[0], nums[1]);
		for (int i = 2; i < nums.size( ); i++)
		{
			res[i] = std::max(res[i - 1], nums[i] + res[i - 2]);
		}

		return res[nums.size( ) - 1];
	}
```