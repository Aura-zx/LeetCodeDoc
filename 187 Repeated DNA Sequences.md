# 187 Repeated DNA Sequences

标签（空格分隔）： LeetCode String Bit_Manipulation

---

**Problem:**
>   All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.
>
Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.
>
For example,
>
Given s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT",
>
Return:
["AAAAACCCCC", "CCCCCAAAAA"].

**Analysis:**

 1. 求给定字符串中出现次数超过一次的长度为10的子串。
 2. 问题比较简单，因为限制了字符的个数和子串的长度，将每一个长度为10的子串作为hash表的key，最后找出那些值大于1的即可。
 3. 具体操作起来，string作为key会超出内存限制，所以有两种将string映射成数字的方法，一种是通过二进制的方式映射，AGCT的二进制表示中后三位是可以区分这四个字符的；另一种是自己设计映射方法，将string映射成一个long型的整数。

**Solution:**
```cpp
	long str2long(std::string s)
	{
		long res = 0;
		for (int i = 0; i < 10; i++)
		{
			if (s[i] == 'A') { res = res * 10 + 1; }
			if (s[i] == 'T') { res = res * 10 + 2; }
			if (s[i] == 'C') { res = res * 10 + 3; }
			if (s[i] == 'G') { res = res * 10 + 4; }
		}

		return res;
	}

	std::string long2str(long idx)
	{
		std::string str = "";
		for (int i = 0; i < 10; i++)
		{
			int d = idx % 10;
			if (d == 1) { str = "A" + str; }
			if (d == 2) { str = "T" + str; }
			if (d == 3) { str = "C" + str; }
			if (d == 4) { str = "G" + str; }
			idx = idx / 10;
		}

		return str;
	}

	std::vector<std::string> findRepeatDnaSequences(std::string s)
	{
		std::map<long, int> m;
		std::vector<std::string> res;
		for (int i = 0; i < s.size( ); i++)
		{
			std::string sub = s.substr(i, 10);
			long idx = str2long(sub);
			if (m.find(idx) == m.end( ))
				m[idx] = 1;
			else
				m[idx]++;
		}

		for (auto i = m.begin( ); i != m.end( ); i++)
		{
			if (i->second > 1)
				res.push_back(long2str(i->first));
		}

		return res;
	}
```
 
