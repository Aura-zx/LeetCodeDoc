# 39 Combination Sum

标签（空格分隔）： LeetCode Backtracking

---

**Problem:**
>   Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.
>
The same repeated number may be chosen from C unlimited number of times.
>
Note:
All numbers (including target) will be positive integers.
Elements in a combination (a1, a2, … , ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).
The solution set must not contain duplicate combinations.
For example, given candidate set 2,3,6,7 and target 7, 
A solution set is: 
[7] 
[2, 2, 3] 

**Analysis:**

 1. 给一个数组和目标数字，求加和能构成目标数字的组合。
 2. 回溯法，注意用到i来控制每次可以访问的数组中的元素，防止重复。
 3. 如例子里的[2,3,6,7]和7
 第一轮 [2] 2367 5
 第二轮 [2 2] 367 3
等等。
 
**Solution:**
```cpp
void backTracking(std::vector<int>& candidates, std::vector<int>& per, int level, std::vector<std::vector<int>>& ret, int target)
	{
		if (target == 0)
		{
			ret.push_back(per);
			return ;
		}

		for (int i = level; i < candidates.size( ); i++)
		{
			if (target - candidates[i] < 0)
				return;
			else
			{
				per.push_back(candidates[i]);
				backTracking(candidates, per, i, ret, target - candidates[i]);
				per.pop_back( );
			}
		}
	}

	std::vector<std::vector<int>> combinationSum(std::vector<int>& candidates, int target)
	{
		std::vector<std::vector<int>> ret;
		std::vector<int> per;

		if (candidates.empty( ) || candidates.size( ) == 0)
			return ret;

		std::sort(candidates.begin(), candidates.end());
		backTracking(candidates, per, 0, ret, target);

		return ret;
	}
```

 
