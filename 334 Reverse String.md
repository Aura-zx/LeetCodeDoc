# 334 Reverse String

标签（空格分隔）： LeetCode 

---

**Problem:**
>   Write a function that takes a string as input and returns the string reversed.

**Analysis:**

 1. 逆序一个字符串。
 

**Solution:**
```cpp
	std::string reverseString(std::string s)
	{
		std::string ret;
		for (auto i = s.rbegin( ); i != s.rend( ); i++)
			ret.push_back(*i);

		return ret;
	}
```

