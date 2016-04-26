# 78 Subsets

标签（空格分隔）： LeetCode Backtracking

---

**Problem:**
>   Given a set of distinct integers, nums, return all possible subsets.
>
Note:
Elements in a subset must be in non-descending order.
The solution set must not contain duplicate subsets.
For example,
If nums = [1,2,3], a solution is:
>
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]

**Analysis:**

 1. 给一个不相同数字的集合，求他们所有的子集。
 2. 回溯法，注意在进入下一层递归时就加入结果中。

**Solution:**
```cpp
	void backtracking(std::vector<int>& nums, std::vector<std::vector<int>>& ret, std::vector<int>& per, int contain)
	{
		for (int i = contain; i < nums.size(); i++)
		{
			per.push_back(nums[i]);
			ret.push_back(per);
			backtracking(nums, ret, per, i+1);
			per.pop_back( );
		}

		return;
	}

	std::vector<std::vector<int>> subsets(std::vector<int>& nums)
	{
		std::vector<std::vector<int>> ret;
		std::vector<int> per;
		ret.push_back(per);
		std::sort(nums.begin( ), nums.end( ));

		backtracking(nums, ret, per, 0);

		return ret;
	}
```
 
