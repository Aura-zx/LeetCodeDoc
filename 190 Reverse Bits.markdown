# 190 Reverse Bits

标签（空格分隔）： LeetCode Bit_Manipulation

---

**Problem:**
>   Reverse bits of a given 32 bits unsigned integer.
>
For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).

**Analysis:**

 1. 反转一串二进制数。
 2. 通过左移和特定位数为1的按位与，控制复制。
 3. 当前数字为1时，给结果+1，同时结果左移1位，最后一位的时候不左移。

**Solution:**
```cpp
	uint32_t reverseBits(uint32_t n)
	{
		uint32_t res  = 0;
		uint32_t mask = 1;
		for (int i = 0; i < 32; i++)
		{
			if (n & mask)
				res = res + 1;
			if (i != 31)
				res <<= 1;
			mask <<= 1;
		}

		return res;
	}
```

