# 28 Implement strStr()

标签（空格分隔）： LeetCode String TwoPointers

---

**Problem:**
>   Implement strStr().
>
Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Analysis:**

 1. strStr(str1, str2)函数的功能是求str2是否是str1的子串，若是则返回str1中的index，不是则返回-1。
 2. 双重循环做即可。

**Solution:**
```cpp
int strStr(std::string haystack, std::string needle)
	{
		int ln = needle.length( );
		int lh = haystack.length( );
		if (!ln) return 0;
		if (!lh) return -1;

		for (int i = 0; i <= lh - ln; i++)
		{
			int n = i;
			for (int j = 0; j < needle.length( ); j++)
			{
				if (haystack[n++] != needle[j])
					break;

				if (j == needle.length( )-1)
					return i;
			}
		}
		return -1;
	}
```
