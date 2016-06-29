# 151 Reverse Word in a Word

标签（空格分隔）： LeetCode String

---

**Problem:**
>   Given an input string, reverse the string word by word.
>
For example,
Given s = "the sky is blue",
return "blue is sky the".

**Analysis:**

 1. 将一个字符串按单词逆序。
 2. 从后向前，分割出每个word，在遇到不是连续的空格的时候，将他们连同一个空格加入到结果中，最后判断第一个字符是不是空格，若不是则将它单独加入结果中，若是则弹出之前加入结果中的空格。

**Solution:**
```cpp
	void reverseWords(std::string &s)
	{
		if (s.empty( ))
			return;

		std::string res;
		std::string word;

		for (int i = s.size( ) - 1; i >= 0; i--)
		{
			if (isspace(s[i]))
			{
				if (i < s.size( ) - 1 && !isspace(s[i + 1]))
				{
					std::reverse(word.begin( ), word.end( ));
					res.append(word+" ");
					word.clear( );
				}
			}
			else
				word.push_back(s[i]);
		}

		if (!isspace(s[0]))
		{
			std::reverse(word.begin( ), word.end( ));
			res.append(word);
		}
		else if (!res.empty( ))
			res.pop_back( );

		s = res;
	}
```
 
