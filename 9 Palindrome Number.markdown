# 9 Palindrome Number

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Determine whether an integer is a palindrome. Do this without extra space.

**Solution:**
```cpp
	bool isPalindrome(int x)
	{
		// negative number is not palindrome
		if (x < 0)
			return false;
		else if (x < 10)		// single number is palindrome
			return true;

		// calculate reverse number
		int tmp = x;
		int reverse = 0;
		while (tmp > 0)
		{
			reverse = reverse * 10 + tmp % 10;
			tmp = tmp / 10;
		}

		// compare with origin number
		if (x == reverse)
			return true;
		else
			return false;
	}
```

**Analysis:**

 1. 题目要求判断一个整形数字是否为回文数
 2. 所有负数都不是回文数，`[0-9]`之间的数都是回文
 3. 其他数字计算他的逆序数，直接比较即可

