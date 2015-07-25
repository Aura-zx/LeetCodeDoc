# 219 Contains Duplicate II

标签（空格分隔）： LeetCode HashTable Array

---

**Problem:**
>Given an array of integers and an integer k, find out whether there there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.

**Solution:**
```cpp
bool containsNearbyDuplicate(vector<int>& nums, int k)
    {
	    // check if nums is empty
		if (nums.empty( ))
			return false;

		map<int, int> m;
		for (size_t i = 0; i < nums.size( ); i++)
		{
			// check first k+1 numbers whether contains duplicate
			if (i <= k)
			{
		    auto p1 = m.insert(pair<int, int>(nums.at(i), nums.at(i)));
				if (p1.second == false)
					return true;
			}
			// check i--k+i numbers whether contains duplicate
			// note: delete the lastest insert element
			else if (i > k)
			{
				m.erase(nums.at(i - k - 1));
				auto p2 = m.insert(pair<int, int>(nums.at(i), nums.at(i)));
				if (p2.second == false)
					return true;
			}
		}
		return false;
	}
```
**Analysis:**

 1. 题意是找出 $k$ 个范围内是否包含重复的数，注意 $i-j<=k$ ,所以 $i$ 到 $j$ 之间有 $k+1$ 个数。
 2. 思路是，先检查`0-k`个元素是否有重复，之后每往前多一个数字，就先`earse`掉`map`中最早插入的数字，再判断当前访问的数字是否重复。


