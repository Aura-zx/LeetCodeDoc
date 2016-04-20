# 343 Integer Break

标签（空格分隔）： LeetCode Math DP

---

**Problem:**
>   Given a positive integer n, break it into the sum of at least two positive integers and maximize the product of those integers. Return the maximum product you can get.
>
For example, given n = 2, return 1 (2 = 1 + 1); given n = 10, return 36 (10 = 3 + 3 + 4).

**Analysis:**

 1. 将一个正数拆分成至少两个正数的和，并使这些正数的乘积最大，返回这个乘积。
 2. DP的方法，当一个数大于3使，将它要么拆成2，要么拆成3，所以可以用DP来做，状态转移方程为f[n]=max(2f[n-2], 3*f[n-3]),f[2] = 2, f[3] = 3。
 3. 为什么2或者3，简单来说，任何一个大于4的数n都可以拆成，n-2和n其中n*(n-2)>n，所以n只能是2或者3；复杂的推断可以利用代数的办法，将n分成(n/x)份，则积为x^(n/x)，求导分析得，使前面的函数达到最大值的x是e。
 4. 2<e<3, 6 = 2+2+2 = 3+3，但是3*3 > 2*2*2所以三个2是不能出现的，优先考虑拆分为3。
 5. 这样就有了O(n)的算法，mod = n%3,mod = 0全是3，mod = 1，4和全是3，mod = 2, 2和全是3。

**Solution:**
```cpp
		if (n <= 3)
			return n - 1;
		std::vector<int> dp(n + 1, 0);
		dp[2] = 2;
		dp[3] = 3;
		for (int i = 4; i < dp.size( ); i++)
			dp[i] = std::max(3 * dp[i - 3], 2 * dp[i - 2]);

		return dp[n];
```
 
**Reference:**
[Why factor 2 or 3?][1]
[Mod 3][2]


  [1]: https://leetcode.com/discuss/98276/why-factor-2-or-3-the-math-behind-this-problem
  [2]: https://www.hrwhisper.me/leetcode-integer-break/