# 191 Number of Bits

标签（空格分隔）： LeetCode Bit_Manipulation

---

**Problem:**
>   Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).
    For example, the 32-bit integer ’11' has binary representation `00000000000000000000000000001011`, so the function should return `3`.

**Analysis:**

 1. 问题求一个整数的二进制表达中1的个数。
 2. 用1通过左移操作和目标数的每一位做与操作，结果不为0时，总数+1。
 3. 可以想到的一个优化是对目标数取log，可以减少1的循环次数。
 4. 由于用了log函数，所以n=0的情况要单独考虑。
 4. 注意循环的边界，循环次数不能超过32。
 
**Solution:**
```cpp
	int hammingWeight(uint32_t n)
	{
		if (n == 0)
			return 0;

		uint32_t res = 0;
		int count = 0;
		for (int i = 0; i < (int)log2f(n) && i < 32; i++)
		{
			res = (1 << i) & n;
			if (res != 0)
				count++;
		}

		return count;
	}
```

