# 40 Combination Sum II

标签（空格分隔）： LeetCode Array Backtracking

---

**Problem:**
>   Given a collection of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.
>
Each number in C may only be used once in the combination.
>
Note:
All numbers (including target) will be positive integers.
Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
The solution set must not contain duplicate combinations.
For example, given candidate set 10,1,2,7,6,1,5 and target 8, 
A solution set is: 
[1, 7] 
[1, 2, 5] 
[2, 6] 
[1, 1, 6] 

**Analysis:**

 1. 给一个数组和目标数字，给出数组中的数能组合成目标数字的组合，不同于I的是这里面的数字只能用一次。
 2. 加入去重复条件if(i > level && candidates[i] == candidate[i-1]) continue; 这是避免了不会有相同的结果出现
 3. 在每一次回溯的时候，将level向前加一个，避开当前数字；这是在每一次循环的时候避开使用重复数字。

**Solution:**
```cpp
	void backtracking(std::vector<int>& candidates, std::vector<int>& per, int level, std::vector<std::vector<int>>& ret, int target)
	{
		if (target == 0)
		{
			ret.push_back(per);
			return ;
		}

		for (int i = level; i < candidates.size( ); i++)
		{
			if (i > level && candidates[i] == candidates[i - 1])
				continue;
			if (target < candidates[i])
				return;

			per.push_back(candidates[i]);
			backtracking(candidates, per, i+1, ret, target - candidates[i]);
			per.pop_back( );
		}
	}

	std::vector<std::vector<int>> combinationSum2(std::vector<int>& candidates, int target)
	{
		std::vector<std::vector<int>> ret;
		std::vector<int> per;

		std::sort(candidates.begin( ), candidates.end( ));

		backtracking(candidates, per, 0, ret, target);

		return ret;
	}
```
 
