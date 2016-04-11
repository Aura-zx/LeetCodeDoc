# 318 Maximum product of word length

标签（空格分隔）： LeetCode Bit_Manipulation

---

**Problem:**
>   Given a string array words, find the maximum value of length(word[i]) * length(word[j]) where the two words do not share common letters. You may assume that each word will contain only lower case letters. If no such two words exist, return 0.
>
Example 1:
Given ["abcw", "baz", "foo", "bar", "xtfn", "abcdef"]
Return 16
The two words can be "abcw", "xtfn".
>
Example 2:
Given ["a", "ab", "abc", "d", "cd", "bcd", "abcd"]
Return 4
The two words can be "ab", "cd".
>
Example 3:
Given ["a", "aa", "aaa", "aaaa"]
Return 0
No such pair of words.

**Analysis:**

 1. 给定一个string数组，求没有相同字符的两个字符串长度相乘的最大值。
 2. 直观的思路是用哈希表映射每个字符串有哪些字符，然后将没有相同的字符串相乘得到最大值。
 3. 位操作版本，将每个字符串映射到int中，对int直接做&操作即可以解决。
 4. max函数使用时会报错，需要将两个参数都统一成int。

**Solution:**
```cpp
	int maxProduct(std::vector<std::string>& words)
	{
		int ret = 0;
		std::vector<int> mask(words.size(), 0);
		for (int i = 0; i < words.size( ); i++)
		{
			for (auto c : words[i])
				mask[i] |= 1 << (c - 'a');

			for (int j = 0; j < i; j++)
			{
				if (!(mask[i] & mask[j]))
					ret = std::max(ret, (int)(words[i].length() * words[j].length()));
			}
		}
		return ret;
	}
```
 
