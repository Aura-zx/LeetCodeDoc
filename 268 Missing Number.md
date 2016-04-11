# 268 Missing Number

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.
>
For example,
Given nums = [0, 1, 3] return 2.

**Analysis:**

 1. 给定一个数组，里面包含n个数从0-n中，求缺少的那一个数。
 2. 题意表明本来有n+1个数，但是只选了n个，求缺少的那一个数，因为给定了长度就给定了整个数字的范围，所以可以得到0-n的和，再减去给定数组的和就得到了缺少的那个数。

**Solution:**
```cpp
	int missingNumber(std::vector<int>& nums)
	{
		int size = nums.size( );
		int total = (0 + size)*(size+1) / 2;
		for (int i = 0; i < size; i++)
			total -= nums[i];

		return total;
	}
```
 
