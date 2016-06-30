# 17 Letter Combinations of a Phone Number

标签（空格分隔）： LeetCode String

---

**Problem:**
>   Given a digit string, return all possible letter combinations that the number could represent.
>
A mapping of digit to letters (just like on the telephone buttons) is given below.
>  
Input:Digit string "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

**Analysis:**

 1. 给一个电话上的数字，求数字对应的字母能组成的所有组合。
 2. 注意这个组合是数字之间的组合，所以首先把第一个数字的字母全部存入结果中，再把第二个数字中的字母每一个和前面的字母相加之后存入结果中。
 3. 即先是{"a","b","c"} -> {"ad", "bd", "cd", "ae", "be", "ce", "af", "bf", "cf"}

**Solution:**
```cpp
    vector<string> letterCombinations(string digits) {
		std::vector<std::string> res;
		if (digits.empty( ))
			return res;
		std::string charmap[10] = { "0", "1", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz" };
		
		res.push_back("");
		for (int i = 0; i < digits.size( ); i++)
		{
			std::vector<std::string> tmp;
			std::string chars = charmap[digits[i] - '0'];
			for (int j = 0; j < chars.size( ); j++)
				for (int k = 0; k < res.size(); k++)
					tmp.push_back(res[k] + chars[j]);
			
			res = tmp;
		}

		return res;
    }
```
 
