# 231 Power of Two

标签（空格分隔）： LeetCode Math Bit_Manipulation

---

**Problem:**
>   Given an integer, write a function to determine if it is a power of two.

**Solution1:**
```cpp
	bool isPowerOfTwo(int n)
	{
		// negative number
		if (n <= 0)
			return false;
		else if (n == 1)	// 2^0 = 1
			return true;
		
		while (1)
		{
			// odd number
			if (n % 2 == 1)
				return false;
			else
				n = n / 2;

			// even number at last
			if (n == 1)
				return true;
		}
	}
```

**Solution2:**
```cpp
	bool isPowerOfTwo(int n)
	{
		// negative number
		if (n <= 0)
			return false;
        
        if ((n & (n-1)) == 0)
            return true;
        else
            return false;
		}
	}
```
**Analysis:**

 1. 题目求判断一个int型是否为2的幂次方
 2. 分情况讨论，负数，奇数除了1以外不是，偶数中除以2之后为奇数的也不是，剩下的全是
 3. Solution2给出了一种位运算的解法，2的幂次数`n`在二进制下和`n-1`按位与之后的结果是`0`

