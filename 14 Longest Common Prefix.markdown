# 14 Longest Common Prefix

标签（空格分隔）： LeetCode String

---
**Problem:**

> Write a function to find the longest common prefix string amongst an array of strings.

**Solution:**
```cpp
	string longestCommonPrefix(vector<string>& strs)
    {
        // return value
		string result = "";
		// first to check if vector is empty
        if (strs.empty())
        {
            return result;
        }
        
		for (size_t i = 0; i < strs.at(0).size( ); i++) // use the first string
		{
			char c = strs.at(0).at(i);
			for (size_t j = 1; j < strs.size( ); j++)   // scan another string with the same index
			{
				if (strs.at(j).size( ) <= i)    // check if i is out of range
				{
					return result;
				}
				else
				{
					if (c != strs.at(j).at(i))
					{
						return result;
					}
				}
			}
			result.append(1, c);    // all the strings pass, add to result
		}
		return result;
	}
```

**Analysis:**

 1. 找strings最长的公共前缀，只需要从前往后对比**相同index**的字符就可以了
 2. 注意判断vector是否为空
 2. 一种思路是直接以第一个string做搜索，但要注意访问越界的问题
 3. 另一种思路是先找到最短的string，以它做搜索，不用注意越界问题，但要多扫描一遍vector

