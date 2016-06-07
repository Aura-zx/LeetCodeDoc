# 201 Bitwise AND of Number Ranges

标签（空格分隔）： LeetCode Bit_Manipulation

---

**Problem:**
>   Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.
>
For example, given the range [5, 7], you should return 4.

**Analysis:**

 1. 题目给一个整数的范围，求这些范围内所有数字与的结果；
 2. 遍历会超时，由数学上的结果，[m,n]范围内数字的结果是m与n公共部分的“左边首部（left header）”；
 3. 将m和n右移，直到他们相等，记录移动的次数，结果就是n向左移相同的次数。
 4. 还有一种方法2中的办法也不会超时，原理是利用了当数字范围内有跨位数的两个数的时候比如7(0111)和8(1000)他们的与的结果是0，所以剩下的就不用算了，减少了计算量。

**Solution:**
```cpp
	int rangeBitwiseAnd(int m, int n)
	{
		for (int i = m+1; i < n; i++)
			m &= i;

		return m & n;
	}

	int rangeBitwiseAnd2(int m, int n)
	{
		while (n > m)
			n = n & n - 1;

		return m & n;
	}

	int rangeBitwiseAnd3(int m, int n)
	{
		int c = 0;
		while (m != n)
		{
			m >> 1;
			n >> 1;
			++c;
		}

		return n << c;
	}
```
  
