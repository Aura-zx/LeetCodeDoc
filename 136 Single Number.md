# 136 Single Number

标签（空格分隔）： LeetCode HashTable Bit_Manipulation

---
**Problem:**
>   Given an array of integers, every element appears twice except for one. Find that single one.
>
Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Analysis:**

 1. 给定一个数组，其他的数字出现两次，找出唯一的出现一次的数。
 2. 直观思路是哈希表，很简单。
 3. 位操作的思路是用异或XOR，比如{2,2,3}这个序列{10,10,11}，10 XOR 10 = 00, 00 XOR 11 = 11。
 4. 起始的时候用0和第一个数字XOR，0和任何数异或等于任何数。

**Solution:**
```cpp
// 直观版本
	int singleNumber(std::vector<int>& nums)
	{
		std::map<int, int> m;
		for (int i = 0; i < nums.size( ); i++)
		{
			if (m.count(nums[i]))
				m[nums[i]]++;
			else
				m[nums[i]] = 1;
		}

		for (auto i : nums)
		{
			if (m[i] == 1)
				return i;
		}
	}
	
// XOR
	int singleNumber(std::vector<int>& nums)
	{
		int x = 0;
		for (auto i : nums)
			x = i ^ x;

		return x;
	}
```
 
