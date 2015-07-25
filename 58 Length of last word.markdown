# 58 Length of last word

标签（空格分隔）： LeetCode String

---

**Problem:**
>   Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.
    
>   If the last word does not exist, return 0.

>   Note: A word is defined as a character sequence consists of non-space characters only.

>   For example, 
>   Given s = "Hello World",
>   return 5.

**Solution:**
```cpp
	int lengthOfLastWord(string s)
	{
		if (s.empty( ))		// check if s is empty
			return 0;

		size_t count = 0;	// length of last word
		bool flag = false;	// flag: if last k-position is space
		for (auto i = s.size( )-1; i >= 0; --i)
		{
			if (s.at(i) != ' ')
			{
				flag = true;	// no space lasts
				count++;
			}
			else if (s.at(i) == ' ' && flag == true)	// have been occured letter
				return count;

			if (i == 0)		// unsigned can't be negative number
				break;
		}

		return count;	// string just contain one word
	}
```
**Analysis:**

 1. 题目要求获取一个`string`中最后一个单词的长度，如果没有单词，返回0
 2. 注意`string`最后的空格都是要忽略的；判断`string`是否为空
 3. 逆序遍历即可
 4. `unsigned`类型在从`0`往下减的时候会得到一个很大的正数，此时循环失效，所以要在循环内增加一个判断