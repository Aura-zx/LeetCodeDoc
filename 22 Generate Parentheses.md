# 22 Generate Parentheses

标签（空格分隔）： LeetCode Backtracking String

---

**Problem:**
>   Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
>
For example, given n = 3, a solution set is:
>
"((()))", "(()())", "(())()", "()(())", "()()()"

**Analysis:**

 1. 给n对括号，求所有合法的组合。
 2. 递归的处理即可，注意左括号数量需要始终大于右括号。
 3. 若是求数量，见Reference，卡特兰数。

**Solution:**
```cpp
	void combinPar(int leftNum, int rightNum, std::string s, std::vector<std::string>& res)
	{
		if (leftNum > rightNum)
			return;

		if (leftNum == 0 && rightNum == 0)
			res.push_back(s);

		if (leftNum > 0)
			combinPar(leftNum - 1, rightNum, s+'(', res);

		if (rightNum > 0)
			combinPar(leftNum, rightNum - 1, s+')', res);
	}

	std::vector<std::string> generateParentheses(int n)
	{
		std::vector<std::string> res;
		std::string s;
		if (n == 0)
			return res;

		combinPar(n, n, s, res);

		return res;
	}
```
 
**Reference:**
[Catalan Number][1]


  [1]: https://www.wikiwand.com/en/Catalan_number