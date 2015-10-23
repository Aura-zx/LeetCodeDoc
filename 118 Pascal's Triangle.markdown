# 118 Pascal's Triangle

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given numRows, generate the first numRows of Pascal's triangle.
>
For example, given numRows = 5,
Return
>
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]

**Analysis:**

 1. 输出给定整数规模的帕斯卡三角形。
 2. 找出规律计算即可。

**Solution:**
```cpp
	std::vector<std::vector<int>> generate(int numRows)
	{
		std::vector<std::vector<int>> res;
		if (numRows <= 0)
			return res;

		for (int i = 1; i <= numRows; i++)
		{	
			std::vector<int> tmp;
			for (int j = 0; j < i; j++)
			{
				if (j == 0 || j == i - 1)
					tmp.push_back(1);
				else
					tmp.push_back(res[i - 2][j - 1] + res[i - 2][j]);
			}
			res.push_back(tmp);
		}

		return res;
	}
```
 
