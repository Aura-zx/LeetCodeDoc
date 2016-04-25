# 241 Different Ways to Add Paraentheses

标签（空格分隔）： LeetCode Divide_and_Conquer

---

**Problem:**
>   Given a string of numbers and operators, return all possible results from computing all the different possible ways to group numbers and operators. The valid operators are +, - and *.
>
Example 1
Input: "2-1-1".
>
((2-1)-1) = 0
(2-(1-1)) = 2
Output: [0, 2]

**Analysis:**

 1. 给一个算式字符串只包含+，-，*三种操作符，求不同的加括号的方法得到式子的值，作为vector返回。
 2. 一开始没有思路，提示里提到了分治的思路，以操作符为界，将字符串分解成子串，再不断把这些子串合起来。
 3. string.substr()中的两个参数分别代表当前的index和需要步进的步数。

**Solution:**
```cpp
	int compute(int a, int b, char op)
	{
		switch (op)
		{
		case'+': return a + b;
		case'-': return a - b;
		case'*': return a * b;
		}
	}

	std::vector<int> diffWaysToCompute(std::string input)
	{
		int number = 0;
		int i = 0;
		for (; i < input.length( ) && isdigit(input[i]); i++)
			number = number * 10 + input[i] - '0';

		// pure number
		if (i == input.length( ))
			return{ number };
		std::vector<int> diffWays;
		std::vector<int> lefts;
		std::vector<int> rights;

		for (int i = 0; i < input.length( ); i++)
		{
			if (isdigit(input[i]))
				continue;
			lefts = diffWaysToCompute(input.substr(0, i));
			rights = diffWaysToCompute(input.substr(i + 1, input.length( ) - i - 1));

			for (int j = 0; j < lefts.size( ); j++)
				for (int k = 0; k < rights.size( ); k++)
					diffWays.push_back(compute(lefts[j], rights[k], input[i]));
		}

		return diffWays;
	}
```
 
