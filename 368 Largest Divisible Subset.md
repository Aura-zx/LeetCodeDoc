# 368 Largest Divisible Subset

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given a set of distinct positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies: Si % Sj = 0 or Sj % Si = 0.
>
If there are multiple solutions, return any subset is fine.
>
Example 1:
nums: [1,2,3]
Result: [1,2] (of course, [1,3] will also be ok)
>
Example 2:
nums: [1,2,4,8]
Result: [1,2,4,8]

**Analysis:**

 1. 给定一个正整数的集合，求他们最大的余数为0的子集。
 2. 首先要知道一个数学原理，当a<b,b%a=0,b<c,c%b=0时，a%c=0。
 3. 设DP[i]为数字i当前的能产生余数为0数字的个数，则当nums[j]满足要求，且DP[i]<DP[j]+1，DP[i]=DP[j]+1。
 4. 同时记录一个index数组，index[i]=j，直接记录和它相关的那个数字，另外维护一个maxdp记录最大的那个数，作为之后遍历index的起点。

**Solution:**
```cpp
	std::vector<int> LargestDivisibleSubset(std::vector<int>& nums)
	{
		std::vector<int> ans;
		if (nums.empty( ))
			return ans;
		std::sort(nums.begin( ), nums.end( ));
		
		auto n = nums.size( );
		std::vector<int> dp(n, 1);
		std::vector<int> index(n, -1);
		int max_index = 0;
		int max_dp = 1;
		for (int i = 0; i < n; i++)
		{
			for (int j = 0; j < i; j++)
			{
				if (nums[i] % nums[j] == 0 && dp[j] + 1 > dp[i])
				{
					dp[i] = dp[j] + 1;
					index[i] = j;
				}
			}
			if (max_dp < dp[i])
			{
				max_dp = dp[i];
				max_index = i;
			}
		}

		for (int i = max_index; i != -1; i = index[i])
			ans.push_back(nums[i]);

		return ans;
	}
```
 
