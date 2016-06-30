# 371 Sum of Two Integers

标签（空格分隔）： LeetCode Bit_Manipulation

---

**Problem:**
>   Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.
>
Example:
Given a = 1 and b = 2, return 3.


**Analysis:**

 1. 求两个数字之和，要求不能用到+和-。
 2. 考虑位操作，异或又称模2和，将每次的最后一位分离出来，通过异或操作加和，维护一个进位量，只要最后两位之间有进位，或者是任意一位和之前的进位量有进位，进位量均置1。
 3. 另一种方法是将a,b之间异或，进位量为他们之间的与，每次循环进位量左移一位，作为新的被加数和之前的结果进行加和，注意在加和之前先得进位量。

**Solution:**
```cpp
    int getSum(int a, int b)
	{
		int ans = 0;
		int carry = 0;

		for (int i = 0; i < 32; a >>= 1, b >>= 1, i++)
		{
			int lower_a = a & 1;
			int lower_b = b & 1;
			ans |= (lower_a ^ lower_b ^carry) << i;
			carry = (carry & lower_a) | (carry & lower_b) | (lower_a & lower_b);
		}

		return ans;
	}

	int getSum2(int a, int b)
	{
		while (b != 0)
		{
			int c = a & b;	// carry
			a ^= b;			// add
			b = c << 1;
		}
		
		return a;
	}
```
 
