# 172 Factorial Trailing Zeroes

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Given an integer n, return the number of trailing zeroes in n!.

**Ananlysis:**

 1. 题目求n！的末尾有几个零。
 2. 只有2和5相乘才会得到零，所以考虑有多少个2和5对。
 3. 仔细考虑发现2>>5，所以只用统计有多少个5即可。
 4. 一开始的想法是遍历1-n，统计有多少个5，因为如25这样的数存在阶乘，结果这种算法会超时。
 5. 其实是一个数学问题，公式如下
 $$f(n) = \sum^k_{i=1}\lfloor \frac{n}{5^i} \rfloor $$

**Solution:**
```cpp
	int trailingZeroes(int n)
	{
		if (n < 5)
			return 0;
		int count = 0;
		while (n >= 5)
		{
			n /= 5;
			count += n;
		}

		return count;
	}
```

**Reference:**
[Trailing Zeroes][1]


  [1]: http://www.wikiwand.com/en/Trailing_zero