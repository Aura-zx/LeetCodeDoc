# 263 Ugly Number

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Write a program to check whether a given number is an ugly number.
    Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.
    Note that 1 is typically treated as an ugly number.

**Solution:**
```cpp
	bool isUgly(int num)
	{
		if (num == 1)
			return true;
		if (num == 0)
			return false;

		while (num % 2 == 0)
			num = num / 2;
		while (num % 3 == 0)
			num = num / 3;
		while (num % 5 == 0)
			num = num / 5;

		if (num == 1)
			return true;
		else
			return false;
	}
```


**Analysis:**

 1. 题目是判断一个数是否为Ugly Number，定义为因子**只有**2,3,5的数为Ugly Number。
 2. 除去1,0单独判断，剩下的只需要当他能被2,3,5整除之时，直接除就可以了，除到最后如果是1则表白只有2,3,5，不是1则表明还有别的因子。

