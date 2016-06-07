# 90 Subsets II

标签（空格分隔）： LeetCode Backtracking

---

**Problem:**
>   Given a collection of integers that might contain duplicates, nums, return all possible subsets.
>
Note: The solution set must not contain duplicate subsets.
>
For example,
If nums = [1,2,2], a solution is:
>   
    [
    [2],
    [1],
    [1,2,2],
    [2,2],
    [1,2],
    []
    ]

**Analysis:**

 1. 给一个有重复数字的数组，求他们能组成的所有子集。
 2. 相比之前的题需要去除重复的数字，如果当前元素和后面的元素相同则跳过这个元素。

**Solution:**
```cpp
	void backtracking(std::vector<int>& nums, std::vector<std::vector<int>>& ret, std::vector<int>& per, int contain)
	{
		for (int i = contain; i < nums.size( ); i++)
		{
			per.push_back(nums[i]);
			ret.push_back(per);
			if (i < nums.size()-1)
				backtracking(nums, ret, per, i + 1);
			per.pop_back( );
			while (i < nums.size( ) - 1 && nums[i] == nums[i + 1])
				i++;
		}

		return;
	}

	std::vector<std::vector<int>> subsetsWithDup(std::vector<int>& nums)
	{
		std::vector<std::vector<int>> ret;
		std::vector<int> per;
		ret.push_back(per);
		std::sort(nums.begin( ), nums.end( ));

		backtracking(nums, ret, per, 0);

		return ret;
	}
```
 
