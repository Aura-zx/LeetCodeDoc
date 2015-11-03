# 290 Word Pattern

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   Given a pattern and a string str, find if str follows the same pattern.
>
Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.
>
Examples:
pattern = "abba", str = "dog cat cat dog" should return true.
pattern = "abba", str = "dog cat cat fish" should return false.
pattern = "aaaa", str = "dog cat cat dog" should return false.
pattern = "abba", str = "dog dog dog dog" should return false.
Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

**Analysis:**

 1. 和205一样，这题变成一个字符对应一个字符串。

**Solution:**
```cpp
bool wordPattern(std::string pattern, std::string str)
	{
		std::map<char, std::string> m1;
		std::map<std::string, char> m2;
		std::vector<std::string> word = getword(str);
		if (word.size( ) != pattern.size( ))
			return false;

		for (int i = 0; i < pattern.size( ); i++)
		{
			char c1 = pattern[i];
			std::string s1 = word[i];

			if (m1.count(c1))
				if (m1[c1] != s1)
					return false;

			if (m2.count(s1))
				if (m2[s1] != c1)
					return false;

			m1[c1] = s1;
			m2[s1] = c1;
		}

		return true;
	}

	std::vector<std::string> getword(std::string str)
	{
		std::vector<std::string> s1;
		std::string tmp;
		for (int i = 0; i < str.size( ); i++)
		{
			if (str[i] != ' ')
				tmp += str[i];
			else
			{
				s1.push_back(tmp);
				tmp.clear( );
			}
		}

		s1.push_back(tmp);
		return s1;
	}
```

