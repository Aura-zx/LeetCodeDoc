# 357 Count Numbers With Unique Digits

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given a non-negative integer n, count all numbers with unique digits, x, where 0 ≤ x < 10n.
>
Example:
Given n = 2, return 91. (The answer should be the total numbers in the range of 0 ≤ x < 100, excluding [11,22,33,44,55,66,77,88,99])
>
Hint:
>
A direct way is to use the backtracking approach.
Backtracking should contains three states which are (the current number, number of steps to get that number and a bitmask which represent which number is marked as visited so far in the current number). Start with state (0,0,0) and count all valid number till we reach number of steps equals to 10n.
This problem can also be solved using a dynamic programming approach and some knowledge of combinatorics.
Let f(k) = count of numbers with unique digits with length equals k.
f(1) = 10, ..., f(k) = 9 * 9 * 8 * ... (9 - k + 2) [The first factor is 9 because a number cannot start with 0].

**Analysis:**

 1. 给一个整数，求整数位数的数字里没有重复数字的数有多少个。
 2. 首先找规律，n=1时，为10个，即0-9个数字，n=2时，第一位有除0外的9个数，第二位有除第一位的9个数，即为9*9个数，f(k) = 9*9*8*...(9-k+2)个数，注意当位数大于10的时候，结果为0，所以不用计算这样的情况。
 3. 设一个一维数组，按照公式计算每一位数的目标要求的数字有多少个，最后把他们加起来即可。

**Solution:**
```cpp
	int countNumbersWithUniqueDigits2(int n)
	{
		// 9-i+2>0 -> i < 11, i最大为10，即当位数大于10的时候，不存在这样的数，所以不用计算这种情况
		n = std::min(n, 10);
		std::vector<int> dp(n + 1, 9);
		dp[0] = 1;
		for (int i = 2; i <= n; i++)
			for (int j = 9; j >= 9 - i + 2; j--)
			{
				dp[i] *= j;
			}

		int ans = 0;
		for (int i = 0; i < dp.size( ); i++)
			ans += dp[i];

		return ans;
	}
```
 
