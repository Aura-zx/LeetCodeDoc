# 46 Permutations

标签（空格分隔）： LeetCode Backtracking

---

**Problem:**
>   Given a collection of distinct numbers, return all possible permutations.
>   
For example,
[1,2,3] have the following permutations:
[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], and [3,2,1].

 **Analysis:**
 

 1. 给定一组不重复的数，给出这些数的全排列。
 2. 采用回溯法，定义两个辅助数组，一个表示当前元素是否使用，一个表示已经用了几个元素。

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
			used[i] = true;
			per.push_back(nums[i]);
			findPermutations(nums, used, per, ret);
			used[i] = false;
			per.pop_back( );
		}
	}

	std::vector<std::vector<int>> permute(std::vector<int>& nums)
	{
		std::vector<std::vector<int>> ret;
		if (nums.empty( ))
			return ret;

		std::vector<bool> used(nums.size(), false);
		std::vector<int> per;
		findPermutations(nums, used, per, ret);

		return ret;
	}
```
 
