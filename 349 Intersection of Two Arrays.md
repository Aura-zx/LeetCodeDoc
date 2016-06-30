# 349 Intersection of Two Arrays

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   Given two arrays, write a function to compute their intersection.
>
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].
>
Note:
Each element in the result must be unique.
The result can be in any order.


**Anaysis:**

 1. 给定两个数组，求两个数组的交集，每个元素必须唯一。
 2. 将第一个数组存入hash表中，遍历第二个数组，发现相同时对值+1，注意这一步不能直接存入结果，因为会有重复的数字影响，最后将表中值不为1的数字存入结果。

**Solution:**
```cpp
	std::vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2)
	{
		std::map<int, int> m;
		std::vector<int> res;
		for (auto i : nums1)
			m[i] = 1;
		
		for (auto i : nums2)
		{
			if (m.find(i) != m.end( ))
				m[i]++;
		}

		for (auto i = m.begin( ); i != m.end( ); i++)
			if (i->second != 1)
				res.push_back(i->first);

		return res;
	}
```

