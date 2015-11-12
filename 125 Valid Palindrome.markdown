# 125 Valid Palindrome

标签（空格分隔）： LeetCode String TwoPointers

---

**Problem:**
>   Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.
>
For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.


**Analysis:**

 1. 判断给定字符串是否是回文字符串，忽略空格、标点、大小写。
 2. 简单思路，字符串预处理，取掉空格，标点，统一大小写，设一头一尾两个指针，分别遍历。
 3. 终止条件为两个index相等或者相差为1。

**Solution:**
```cpp
	bool isPalindrome(std::string s)
	{
		if (s.empty( ) || (s.length( ) == 1))
			return true;

		std::string ss = "";
		for (auto c : s)
			if (isalnum(c))
				ss += ::toupper(c);

		if (ss.empty( ))
			return true;
		int i = 0;
		int j = ss.length()-1;
		while (i != j)
		{
			if (ss[i] != ss[j])
				return false;
			if (i == j || (j - i == 1))
				break;
			else
			{
				i++;
				j--;
			}
		}
		return true;
	}
```
 
