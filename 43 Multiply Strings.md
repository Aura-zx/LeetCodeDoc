# 43 Multiply Strings

标签（空格分隔）： LeetCode String

---

**Problem:**
>   Given two numbers represented as strings, return multiplication of the numbers as a string.
>
Note:
The numbers can be arbitrarily large and are non-negative.
Converting the input string to integer is NOT allowed.
You should NOT use internal library such as BigInteger.

**Analysis:**
 
 0. 两个字符串相乘时乘数和结果之间的下标关系：n1[i] * n2[j] = result[i+j+1]
 1. 用字符串完成大数的乘法。
 2. 考虑正常两个数字的乘法过程，按照过程计算即可。
 3. 因为在乘的过程中，需要加上目标位置当前的数字，需要考虑进来，剩下的carry的设置和处理和#2问题是一致的。
 4. 最后还需要注意的是对0的处理，当9999*0时，不处理给出的结果是0000，但是目标答案是0，需要做处理。

**Solution:**
```cpp
	std::string multiply(std::string num1, std::string num2)
	{
		if (num1.size( ) == 0 || num2.size( ) == 0)
			return 0;
		std::string res(num1.size( ) + num2.size( ), '0');
		std::reverse(num1.begin( ), num1.end( ));
		std::reverse(num2.begin( ), num2.end( ));

		for (int i = 0; i < num1.size( ); i++)
		{
			int dig1 = num1[i] - '0';
			int carry = 0;
			for (int j = 0; j < num2.size( ); j++)
			{
				int dig2 = num2[j] - '0';
				int exist = res[i + j] - '0';
				res[i + j] = (dig1*dig2 + carry + exist) % 10 + '0';
				carry = (dig1*dig2 + carry + exist) / 10;
			}

			if (carry > 0)
				res[i + num2.size( )] = carry + '0';
		}

		std::reverse(res.begin( ), res.end( ));
		int start = 0;
		while (res[start] == '0' && start < res.size( ))
			start++;

		if (start == res.size( ))
			return "0";

		return res.substr(start, res.size( ) - start);
	}
```
 
