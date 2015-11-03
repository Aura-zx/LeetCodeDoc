# 205 Isomorphic Strings

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   Given two strings s and t, determine if they are isomorphic.
>
Two strings are isomorphic if the characters in s can be replaced to get t.
>
All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.
>
For example,
Given "egg", "add", return true.
>
Given "foo", "bar", return false.
>
Given "paper", "title", return true.
>
Note:
You may assume both s and t have the same length.

**Analysis:**

 1. 判断两个字符串是否同构，也就是对应的模式是否一样。
 2. 利用哈希表来做，同时获得两个字符串当前的字符，检索哈希表看是否一样。

**Solution:**
```cpp
	bool isIsomorphic(std::string s, std::string t)
	{
		std::map<char,char> ms;
		std::map<char,char> mt;
		for (size_t i = 0; i < s.size( ); i++)
		{
			char c1 = s[i];
			char c2 = t[i];
			if (ms.count(c1))
			{
				if (ms[c1] != c2)
					return false;
			}
			if (mt.count(c2))
			{
				if (mt[c2] != c1)
					return false;
			}
			ms[c1] = c2;
			mt[c2] = c1;
		}

		return true;
	}
```
 
