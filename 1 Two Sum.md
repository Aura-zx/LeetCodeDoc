# 1 Two Sum

标签（空格分隔）： LeetCode HashTable Array

---

**Problem：**
>   Given an array of integers, return indices of the two numbers such that they add up to a specific target.
>
    You may assume that each input would have exactly one solution.
>
Example:
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

**Analysis:**

 1. 题目给定一个数组和数，求数组里哪两个数的和是目标数字，返回他们的序号。
 2. 哈希表可以完美处理问题，思路也很简单。
 3. 不要一开始就把数字和序号存入哈希表，这样会导致查找失败比如target=6，而数组里有3就会出现问题。
 4. 同时还能解决同一个数字出现两次的问题比如{0,3,4,0}和0这组case。

**Solution:**
```cpp
	std::vector<int> twoSum(std::vector<int>& nums, int target)
	{
		std::map<int, int> m1;
		std::vector<int> ret;

		for (int i = 0; i < nums.size( ); i++)
		{
			if (m1.find(target - nums[i]) != m1.end( ))
			{
				ret.push_back(m1[target - nums[i]]);
				ret.push_back(i);
				return ret;
			}				
			m1[nums[i]] = i;
		}
		return ret;
	}
```