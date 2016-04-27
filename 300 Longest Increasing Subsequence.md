# 300 Longest Increasing Subsequence

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given an unsorted array of integers, find the length of longest increasing subsequence.
>
For example,
Given [10, 9, 2, 5, 3, 7, 101, 18],
The longest increasing subsequence is [2, 3, 7, 101], therefore the length is 4. Note that there may be more than one LIS combination, it is only necessary for you to return the length.
>
Your algorithm should run in O(n2) complexity.
>
Follow up: Could you improve it to O(n log n) time complexity?

**Analysis:**

 1. 给一个无序数组，求里面最长的升序序列的长度。
 2. 遍历整个数组，依次找各个元素之前的最长序列，取最长的，DP[i] = max(DP[i],DP[j]+1)(nums[i]>nums[j])

**Solution:**
```cpp
	int lengthOfLIS(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;

		std::vector<int> dp(nums.size( ), 1);

		for (int i = 0; i < nums.size( ); i++)
			for (int j = 0; j < i; j++)
			{
				if (nums[i] > nums[j])
					dp[i] = std::max(dp[i], dp[j] + 1);
			}

		return *std::max_element(dp.begin(), dp.end());
	}
```