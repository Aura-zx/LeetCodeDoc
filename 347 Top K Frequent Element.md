# 347 Top K Frequent Element

标签（空格分隔）： LeetCode HashTable Heap

---

**Problem:**
>   Given a non-empty array of integers, return the k most frequent elements.
>
For example,
Given [1,1,1,2,2,3] and k = 2, return [1,2].
>
Note: 
You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
Your algorithm's time complexity must be better than O(n log n), where n is the array's size.


**Analysis:**

 1. 求一个数组中，出现次数最多的前K个数。
 2. 遍历数组，建立hash表，记录每个数字出现的次数，将这些次数排序，得到最后的结果。
 3. map默认按key排序，但题目需要对value排序，要自己写。
 4. 注意代码中cmp的写法，这里创建了一个functional对象，用于sort排序中的比较，大于号表示是升序。
 5. 对map按value排序需要将map中的pair放入vector再在vector中用algorithm库中的算法排序。


**Solution:**
```cpp
	std::vector<int> topKFrequent(std::vector<int>& nums, int k)
	{
		std::map<int, int> m;
		std::vector<std::pair<int, int>> p;
		std::vector<int> ret;

		auto cmp = [](std::pair<int, int> const &a, std::pair<int, int> const &b)
		{
			return a.second > b.second;
		};

		for (int i = 0; i < nums.size( ); i++)
		{
			if (m.count(nums[i]))
				m[nums[i]]++;
			else
				m[nums[i]] = 1;
		}

		for (auto i = m.rbegin(); i != m.rend(); i++)
			p.push_back((*i));

		sort(p.begin( ), p.end( ), cmp);

		for (int i = 0; i < k; i++)
		{
			ret.push_back(p[i].first);
		}
		return ret;
	}
```
 
