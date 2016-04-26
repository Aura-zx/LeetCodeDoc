# 77 Combiantions

标签（空格分隔）： LeetCode Backtracking

---

**Porblem:**
>   Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.
>
For example,
If n = 4 and k = 2, a solution is:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]

**Analysis:**

 1. 给出1-n的所有k个的组合。
 2. 回溯法做，核心思路是控制下一层回溯的初始值，保证不会出现重复。

**Solution:**
```cpp
	void backtracking(std::vector<std::vector<int>>& ret, std::vector<int>& per, int n, int k, int start)
	{
		if (per.size( ) == k)
		{
			ret.push_back(per);
			return;
		}
			
		for (int i = start; i <= n; i++)
		{
			per.push_back(i);
			backtracking(ret, per, n, k, i+1);
			per.pop_back( );
		}
	}

	std::vector<std::vector<int>> combine(int n, int k)
	{
		std::vector<std::vector<int>> ret;
		std::vector<int> per;
		
		backtracking(ret, per, n, k, 1);

		return ret;
	}
```
 
