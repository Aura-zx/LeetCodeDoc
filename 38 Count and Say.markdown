# 38 Count and Say

标签（空格分隔）： LeetCode String

---

**Problem:**
>   The count-and-say sequence is the sequence of integers beginning as follows:
1, 11, 21, 1211, 111221, ...
>
1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
Given an integer n, generate the nth sequence.
>
Note: The sequence of integers will be represented as a string.


**Analysis:**

 1. 理解题意很重要，简单来说，在数字前面加上它的量词，对于连续的多个数字则相当于压缩了。
 2. 模拟这个机制即可。

**Solution:**
```cpp
	std::string countAndSay(int n)
	{
		if (n < 1)
			return "";
		std::string prev = "1";

		for (int i = 2; i <= n; i++)
		{
			char curchar = prev[0];
			int times = 1;
			std::string tmp;
			prev.push_back('#');
			for (int k = 1; k < prev.size( ); k++)
			{
				if (prev[k] == curchar)
					times++;
				else
				{
					tmp += std::to_string(times);
					tmp.push_back(curchar);
					curchar = prev[k];
					times = 1;
				}
			}
			prev = tmp;
		}

		return prev;
	}
```
 
