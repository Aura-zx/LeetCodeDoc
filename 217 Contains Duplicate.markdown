# 217 Contains Duplicate

标签（空格分隔）： LeetCode Array HashTable

---

**Problem:**

> Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**Solution:**
```cpp
	bool  containsDuplicate(vector<int>& nums)
	{
		// check if nums is empty
		if (nums.empty( ))
			return false;

		// use map to hash
		map<int, int> m1;
		pair<map<int, int>::iterator, bool> p1;

		for (size_t i = 0; i < nums.size( ); i++)
		{
			p1 = m1.insert(pair<int, int>(nums.at(i), nums.at(i)));
			if (p1.second == false)
				return true;
		}
		return false;
	}
```
**Analysis:**

 1. 题目大意是判断一个vector中有没有重复的数
 2. 思路一：选择一个数，遍历vector比较有没有重复的数，算法复杂度O(n^2)
 3. 思路二: 构建Hash Table，在构建的过程中，只要冲突就表明有重复；构建成功就表明没有重复。
 
**Technical Details：**
`map<int, int>`插入的值是`pair<int, int>`
返回值是`pair<map<int, int>::iterator, bool>`
所以在判断插入是否成功时，判断`pair.second`的值就可以了
