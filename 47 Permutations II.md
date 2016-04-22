# 47 Permutations II

标签（空格分隔）： LeetCode Backtracking

---

**Problem:**
>   Given a collection of numbers that might contain duplicates, return all possible unique permutations.
>
For example,
[1,1,2] have the following unique permutations:
[1,1,2], [1,2,1], and [2,1,1].

**Analysis:**

 1. 和1不同的是有重复的元素在。
 2. 通过排序和去重复得到最终的结果，去重复的数字是那些在当前递归层和前一个数字一样但没有被使用的数字。

**Solution:**
```cpp
	void findPermutations(std::vector<int>& nums, std::vector<bool>& used, std::vector<int>& per, std::vector<std::vector<int>>& ret)
	{
		if (per.size( ) == nums.size( ))
		{
			ret.push_back(per);
			return;
		}

		for (int i = 0; i < nums.size( ); i++)
		{
			if (used[i])
				continue;
			if (i > 0 && nums[i] == nums[i - 1] && !used[i - 1])
				continue;
			used[i] = true;
			per.push_back(nums[i]);
			findPermutations(nums, used, per, ret);
			used[i] = false;
			per.pop_back( );
		}
	}

	std::vector<std::vector<int>> permuteUnique(std::vector<int>& nums)
	{
		std::vector<std::vector<int>> ret;
	
		if (nums.empty( ))
			return ret;
		std::sort(nums.begin(), nums.end());
		std::vector<bool> used(nums.size( ), false);
		std::vector<int> per;
		findPermutations(nums, used, per, ret);
		
		return ret;
	}
```
**Reference:**
[一个解答][1]


  [1]: http://bangbingsyb.blogspot.com/2014/11/leetcode-permutations-i-ii.html