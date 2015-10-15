# 171 Excel Sheet Column Number

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Related to question Excel Sheet Column Title
    Given a column title as appear in an Excel sheet, return its corresponding column number.
>
For example:
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 

**Anlysis:**

 1. 一个基于excel的题，将他表示Sheet的符号转换成数字。
 2. 实际是一个进制转换问题，将26进制的数字转换成10进制。
 3. 比较简单，注意int的表示范围，过程中需要用long double类型。

**Soultion:**
```cpp
	int titleToNumber(std::string s)
	{
		if (s.empty( ))
			return 0;

		long double sum = 0;			// int will out of range
		int base = 0;
		int exp = 0;
		for (size_t i = 0; i < s.length(); i++)
		{
			base = s[i] - 'A' + 1;
			exp = s.length( ) - i - 1;
			std::cout << base << "*26^" << exp << std::endl;    // test
			sum += base*powf(26, exp);
		}

		return sum;
	}
```

