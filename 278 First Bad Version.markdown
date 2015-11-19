# 278 First Bad Version

标签（空格分隔）： LeetCode BinarySearch

---

**Problem:**
>   You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.
>
Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.
>
You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

**Analysis:**

 1. 题目求数列中第一个坏的数，坏的数之后都是坏的数。
 2. 二分法思路，默认1和n分别为好的数和坏的数，单独判断1是否为坏的数。
 3. 注意求mid值时不要溢出，采用`mid=low+(high-low)/2`。
 
**Solution:**
```cpp
int firstBadVersion(int n)
	{
		if (isBadVersion(1))
			return 1;

		int t = 1;
		int f = n;
		int mid = t + (f - t) / 2;

		while (t != f && (f - t != 1))
		{
			if (isBadVersion(mid))
			{
				f = mid;
				mid = t + (f - t) / 2;
			}
			else
			{
				t = mid;
				mid = t + (f - t) / 2;
			}
		}

		return f;
	}
```

