# 67 Add Binary

标签（空格分隔）： LeetCode String Math

---

**Problem:**
>   Given two binary strings, return their sum (also a binary string).
>
For example,
a = "11"
b = "1"
Return "100".

**Analysis:**

 1. 对两个二进制字符串相加，模拟该机制即可。
 
**Solution:**
```cpp
std::string addBinary(std::string a, std::string b)
	{
		if (a.empty( ) && b.empty( ))
			return "";

		std::string res;
		int high = 0;
		auto i = a.rbegin( );
		auto j = b.rbegin( );
		for (; i != a.rend( ) && j != b.rend( ); i++, j++)
		{
			if (high == 0)
			{
				if ((*i) == '1' && (*j) == '1')
				{
					high = 1;
					res.push_back('0');
				}
				else if ((*i) == '0' && (*j) == '0')
				{
					high = 0;
					res.push_back('0');
				}
				else
				{
					high = 0;
					res.push_back('1');
				}
			}
			else
			{
				if ((*i) == '1' && (*j) == '1')
				{
					high = 1;
					res.push_back('1');
				}
				else if ((*i) == '0' && (*j) == '0')
				{
					high = 0;
					res.push_back('1');
				}
				else
				{
					high = 1;
					res.push_back('0');
				}
			}
		}

		decltype(i) k;
		decltype(i) ek;

		if (i == a.rend( ))
		{
			k = j;
			ek = b.rend( );
		}
		else
		{
			k = i;
			ek = a.rend( );
		}

		if (high != 1)
			res.insert(res.end( ), k, ek);
		else
		{
			for (; k != ek; k++)
			{
				if ((*k) == '1')
				{
					high = 1;
					res.push_back('0');
				}
				else
				{
					high = 0;
					res.push_back('1');
					res.insert(res.end( ), k + 1, ek);
					break;
				}
			}
		}
		if (high == 1)
			res.push_back('1');

		reverse(res.begin(), res.end());

		return res;
	}
```

