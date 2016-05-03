# 313 Super Ugly Number

标签（空格分隔）： LeetCode Math Heap

---

**Problem:**
>   Write a program to find the n-th super ugly number.
>
Super ugly numbers are positive numbers whose all prime factors are in the given prime list primes of size k. For example, [1, 2, 4, 7, 8, 13, 14, 16, 19, 26, 28, 32] is the sequence of the first 12 super ugly numbers given primes = [2, 7, 13, 19] of size 4.


**Analysis:**

 1. 求以特定质数序列构成的ugly数的升序序列特定的一个数。
 2. 比ugly II问题更进一步，构成ugly number的质数不再是2,3,5而是一个特定的序列，还是按照ugly II中的解法，只需要将固定的point变成vector就可以了。

**Solution:**
```cpp
int nthSuperUglyNumber(int n, std::vector<int>& primes)
	{
		std::vector<int> ugly = { 1 };
		std::vector<int> point(primes.size(), 0);

		if (n == 1)
			return ugly[0];
		
		while (ugly.size( ) < n)
		{		
			int minv = INT_MAX;
			int mini = 0;

			for (int i = 0; i < primes.size( ); i++)
			{
				int tmp = ugly[point[i]] * primes[i];
				if (tmp < minv)
				{
					minv = tmp;
					mini = i;
				}
			}
			point[mini]++;

			if (minv != ugly.back( ))
				ugly.push_back(minv);
		}

		return ugly[n - 1];
```
 
