# 89 Gray Code

标签（空格分隔）： LeetCode Backtrcking

---

**Problem:**
>   The gray code is a binary numeral system where two successive values differ in only one bit.
>
Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.
>
For example, given n = 2, return [0,1,3,2]. Its gray code sequence is:
>
00 - 0
01 - 1
11 - 3
10 - 2

**Analysis:**

 1. 给一个n值，将n位的gray code输出。
 2. 见Reference的解释，根据gray code的生成方式，n位的gray code是n-1位的它逆序在最高位+1即可

**Solution:**
```cpp
	std::vector<int> grayCode(int n)
	{
		std::vector<int> result;
		result.push_back(0);
		for (int i = 0; i < n; i++)
		{
			int highestBit = 1 << i;
			int len = result.size( );
			for (int i = len - 1; i >= 0; i--)
				result.push_back(highestBit + result[i]);
		}

		return result;
	}
```
 
**Reference：**
[Gray Code][1]


  [1]: https://www.wikiwand.com/en/Gray_code