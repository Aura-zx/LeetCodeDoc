# 8 String To Integer

标签（空格分隔）： LeetCode Math String

---

**Problem:**
>   Implement atoi to convert a string to an integer.

**Analysis:**

 1. 题目要求实现一个函数把String类型转换为int型。
 2. 首先考虑前面的空格，其次是符号如`+`,`-`,只能出现一个，多余则为非法字符串。
 3. 其次若字符串中间有空格，则只考虑空格前的字符串。


**Solution:**
```cpp
	int myAtoi(std::string str)
	{
		if (str.length() == 0)
			return 0;

		long long result = 0;
		int sign = 1;
		int i = 0;
		while (str[i] == ' ')
		{
			i++;
		}

		if (str[i] == '+')
			i++;
		else if (str[i] == '-')
		{
			sign = -1;
			i++;
		}

		for (int j = i; j < str.length( ); j++)
		{
			if (str[j] >= '0' && str[j] <= '9')
			{
				result = result * 10 + str[j] - '0';
				if (result > INT_MAX)
					return sign < 0 ? INT_MAX : INT_MIN;
			}
			else
				break;
		}

		result *= sign;
		return (int)result;
	}
```
 
