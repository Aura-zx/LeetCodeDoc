# 303 Range Sum Query-Immutable

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.
>
Example:
Given nums = [-2, 0, 3, -5, 2, -1]
>
sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
Note:
You may assume that the array does not change.
There are many calls to sumRange function.

**Analysis:**

 1. 题目要求一个vector中给定范围的数字的和。
 2. 简单的想法是循环相加，但这个方法在这个题中会LTE，所有得换一种思路。
 3. 注意到这次的题目给出了类的构造函数，所以可以在构造函数中做提前的运算。
 4. 核心思路是若要计算2-3的和，就用0-3的和减去0-2的和。

**Solution:**
```cpp
class NumArray
{
	std::vector<int> ret = { 0 };
public:
	NumArray(std::vector<int> &nums)
	{
		for (auto n : nums)
			ret.push_back(ret.back( ) + n);
	}

	int sumRange(int i, int j)
	{
		return ret[j + 1] - ret[i];
	}
};
```

