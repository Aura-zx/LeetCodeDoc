# 128 Longest Consecutive Sequence

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   Given an unsorted array of integers, find the length of the longest consecutive elements sequence.
>
For example,
Given [100, 4, 200, 1, 3, 2],
The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.
>
Your algorithm should run in O(n) complexity.

**Analysis:**

 1. 给定一个无序数组，求它的最长连续元素序列，要求O(N)；
 2. 用哈希表结构，注意用map会超时，所以选用unordered_set。
 3. 对数组中的每一个数字先找大于它的数字是否存在，然后接着找小于它的数字，计算当前sequence的长度，对每一个数字都计算这样的长度，取他们的最大值。


**Solution:**
```cpp
	int longestConsecutive(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;
		std::unordered_set<int> m;
		for (auto i : nums)
			m.insert(i);

		int maxlen = 1;
		for (int i = 0; i < nums.size( ); i++)
		{
			if (m.empty( ))
				break;
			int curlen = 0;
			int curnum = nums[i];
			
			// 取掉重复的数字
			while (m.count(curnum))
			{
				m.erase(curnum);
				curlen++;
				curnum++;
			}

			// 找比当前数字小的数字
			curnum = nums[i] - 1;
			while (m.count(curnum))
			{
				m.erase(curnum);
				curlen++;
				curnum--;
			}

			maxlen = std::max(maxlen, curlen);
		}

		return maxlen;
	}
```

 
