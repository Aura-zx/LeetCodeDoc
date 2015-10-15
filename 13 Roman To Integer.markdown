# 13 Roman To Integer

标签（空格分隔）： LeetCode Math String

---

**Problem:**
>   Given a roman numeral, convert it to an integer.
    Input is guaranteed to be within the range from 1 to 3999.

**Analysis:**

 1. 将罗马数字转换为整数。
 2. 
基本字符	
I ——1
V ——5
X ——10
L ——50
C ——100
D ——500
M ——1000
 3. M    C   M   L   X   X   V   I－1976
    |    |   |   |   |   |   |   |
  1000  100 1000 50  10  10  5   1
1000-100+1000+50+10+10+5+1 = 1976
 4. 思路是遍历整个字符串，若是后面的字符小于前面的字符，则减去这个字符代表的数字，反之则加上。

**Solution:**
```cpp
	int romanToInt(std::string s)
	{
		if (s.empty( ))
			return 0;

		int result = 0;
		std::map<char, int> roman;
		roman['I'] = 1;
		roman['V'] = 5;
		roman['X'] = 10;
		roman['L'] = 50;
		roman['C'] = 100;
		roman['D'] = 500;
		roman['M'] = 1000;

		for (int i = s.length( )-1; i >= 0; i--)
		{
			if (i == s.length( ) - 1)
			{
				result = roman[s[i]];
				continue;
			}
			if (roman[s[i]] >= roman[s[i + 1]])
				result += roman[s[i]];
			else
				result -= roman[s[i]];
		}

		return result;
	}
```

