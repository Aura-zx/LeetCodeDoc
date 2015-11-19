# 168 EXCEL SHEET COLUMN TITLE

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Given a positive integer, return its corresponding column title as appear in an Excel sheet.
>
For example:
>
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 

**Analysis:**

 1. 将整数转换成Excel的列表示。
 2. 就是将十进制转换成26进制。
 3. 下标从1开始，所以在最后要(n-1)/26。

**Solution:**
```cpp
	std::string convertToTitle(int n)
	{
		std::string res = "";
		if (n <= 0)
			return res;

		while (n != 0)
		{
			int low = n % 26;
			if (low == 0)
				res += 'Z';
			else
				res += 'A' + low-1;
			n = (n-1) / 26;
		}
		
		reverse(res.begin( ), res.end( ));

		return res;
	}
```

