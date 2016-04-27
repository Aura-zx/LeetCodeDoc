# 264 Ugly Number II

标签（空格分隔）： LeetCode DP Math

---

**Problem:**
>   Write a program to find the n-th ugly number.
>
Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.
>
Note that 1 is typically treated as an ugly number.

**Analysis:**

 1. 找出第n个Ugly Number。
 2. 维护三个变量分别是当前ugly numberx2，x3，x5之后的数，将其中最小的压入数组，直到数组size满足要求的n。
 3. 程序中p2,p3,p4很巧妙，相当于记录了三个链表的最后一个节点，while循环中的if去除了重复的数。

**Solution:**
```cpp
	int nthUglyNumber(int n)
	{	
		std::vector<int> ugly =  { 1 };

		if (n == 1)
			return ugly[0];

		int minv;
		
		int p2 = 0;
		int p3 = 0;
		int p5 = 0;

		while (ugly.size() < n)
		{
			int ugly2 = ugly[p2] * 2;
			int ugly3 = ugly[p3] * 3;
			int ugly5 = ugly[p5] * 5;

			minv = std::min(ugly2, std::min(ugly3, ugly5));
			if (minv == ugly2)
				p2++;
			if (minv == ugly3)
				p3++;
			if (minv == ugly5)
				p5++;

			if (minv != ugly.back())	// 去除重复的数字
				ugly.push_back(minv);
		}
		
		return ugly[n - 1];
	}
```