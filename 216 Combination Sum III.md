# 216 Combination Sum III

标签（空格分隔）： LeetCode Array Backtracking

---

**Problem:**
>   Find all possible combinations of k numbers that add up to a number n, given that only numbers from 1 to 9 can be used and each combination should be a unique set of numbers.
>
Ensure that numbers within the set are sorted in ascending order.
>
Example 1:
>
Input: k = 3, n = 7
>
Output:
>
[[1,2,4]]
>
Example 2:
>
Input: k = 3, n = 9
>
Output:
>
[[1,2,6], [1,3,5], [2,3,4]]

**Analysis:**

 1. 求在1-9中能组成数n的k个数的所有组合。
 2. 和之前的程序基本一致，仅需要在回溯中返回中加上判断是否是k个数字即可。

**Solution:**
```cpp

	void backtracking(std::vector<std::vector<int>>& ret, std::vector<int>& candidates, std::vector<int>& per, int level, int target, int lim)
	{
		if (target == 0 && lim == per.size())
		{
			ret.push_back(per);
			return;
		}

		for (int i = level; i < candidates.size( ); i++)
		{
			if (i > level && candidates[i] == candidates[i - 1])
				return;
			if (target < candidates[i])
				return; 
			per.push_back(candidates[i]);
			backtracking(ret, candidates, per, i + 1, target - candidates[i], lim);
			per.pop_back( );
		}
	}

	std::vector<std::vector<int>> combinationSum3(int k, int n)
	{
		std::vector<int> candidates = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
		std::vector<std::vector<int>> ret;
		std::vector<int> per;

		backtracking(ret, candidates, per, 0, n, k);

		return ret;
	}
```
 
