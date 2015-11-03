# 20 Valid Parentheses

标签（空格分隔）： LeetCode Stack

---

**Problem:**
>   Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
>
The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

**Analysis:**

 1. 判断一个全是括号组合的字符串的括号能否匹配。
 2. 使用栈，左括号入栈，右括号判断
    1）栈的是否为空
    2）top元素是否匹配

**Solution:**
```cpp
bool isValid(std::string s)
	{
		if (s.empty( ))
			return false;

		std::stack<char> ps;
		ps.push(s[0]);
		for (size_t i = 1; i < s.size( ); i++)
		{
			if (s[i] == '(' || s[i] == '[' || s[i] == '{')
			{
				ps.push(s[i]);
				continue;
			}

			if (ps.size( ) == 0)		// too much ')' && '}' && ']'
				return false;
			char current = ps.top();
			if (s[i] == ')' && current != '(')
				return false;
			if (s[i] == ']' && current != '[')
				return false;
			if (s[i] == '}' && current != '{')
				return false;
			ps.pop();
		}

		if (ps.size( ) != 0)
			return false;

		return true;
	}
```

