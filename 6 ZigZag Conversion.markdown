# 6 ZigZag Conversion

标签（空格分隔）： LeetCode String

---

**Problem:**
>   The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
>
    P   A   H   N
    A P L S I I G
    Y   I   R
    And then read line by line: "PAHNAPLSIIGYIR"
    Write the code that will take a string and make this conversion given a number of rows:
    string convert(string text, int nRows);
    convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR".

**Solution:**
```cpp
	std::string convert(std::string s, int numRows)
	{
		if (s.empty( ) || numRows == 1 ||s.length() <= numRows)
			return s;
		int zigspan = 2 * numRows - 2;
		
		std::string res;
		for (int i = 0; i < numRows; i++)
		{
			for (int j = i; j < s.length( ); j += zigspan)
			{
				res.push_back(s[j]);					// fixed number for each row
				if (i != 0 && i != numRows-1 && j + zigspan - 2 * i < s.length( ))  // not 1st row and last-1 row and in range
					res.push_back(s[j + zigspan - 2 * i]);
			}
		}
		return res;
	}
```
**Analysis:**

 1. 本题是将字符串按照ZigZag形式重新排列后，从左至右依次读取构成新的字符串，求这个新的字符串。

    ```cpp
      01     07      13
      02  06 08   12 14   18
      03 05  09 11   15 17
      04     10      16
    ```

 2. 由上图可以看出，第一行和最后一行的字符串的间隔是固定的，其他行在两列之间的间隔也是有规律的，
    根据行不同有不同的间隔。

 3. 思路是首尾行一起处理，其他行按规律计算，同一行中每两列之间间隔也是固定的。
 4. 每行的固定间隔是`2*row-2`,其他行的浮动间隔是`2*row-2-2*i`,`i`是行数。

