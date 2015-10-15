# 70 Climbing Stairs

标签（空格分隔）： LeetCode Dynamic_Programming

---

**Problem:**
>   You are climbing a stair case. It takes n steps to reach to the top.
    Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Analysis:**

 1. 爬楼梯问题，有1步和2步两种方案，求到第n层有多少种方法。
 2. 动态规划方法，到第n层的方法=第n-1层的方法+第n-2层的方法
 3. s[n] = s[n-1]+s[n-2]
 4. s[1] = 1; s[2] = 2;


**Solution:**
```cpp
	int climbStairs(int n)
	{
		if (n <= 2)
			return n;
		else
		{
			int* step = new int[n];

			step[0] = 1;
			step[1] = 2;

			for (int i = 2; i < n; i++)
				step[i] = step[i - 1] + step[i - 2];

			return step[n - 1];
		}
	}
```

