# 228 Summary Ranges

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given a sorted integer array without duplicates, return the summary of its ranges.

>   For example, given [0,1,2,4,5,7], return ["0->2","4->5","7"].

**Solution:**
```cpp
vector<string> summaryRanges(vector<int> &nums)
	{
		vector<string> res = {};
		if (nums.empty() == true)
		{
			return res;
		}
		size_t i = 0;
		size_t j = 0;
		int lf = 0;								// 0 is single numbewr. 1 is b->e form.
		int b;
		for (i = 0; i < nums.size( ); i=j+1)
		{
			b = nums.at(i);
			lf = 0;
			for (j = i; j < nums.size( ); j++)
			{
				int cur = nums.at(j);
				if (j == nums.size( )-1)				// corner case: the last element
				{
					if (lf == 1)
					{
						string s1 = to_string(b);
						string s2 = to_string(cur);
						string tmp = s1 + "->" + s2;
						res.push_back(tmp);
						break;
					}
					else
					{
						string s1 = to_string(cur);
						res.push_back(s1);
						break;
					}
				}
				int tar = nums.at(j + 1);
				if (cur + 1 == tar)
				{
					lf = 1;			
					continue;
				}
				else
				{
					if (lf == 0)
					{
						string s1 = to_string(cur);
						res.push_back(s1);
						break;
					}
					else
					{
						string s1 = to_string(b);
						string s2 = to_string(cur);
						string tmp = s1 + "->" + s2;
						res.push_back(tmp);
						break;
					}
				}
			}
		}
		return res;
	}
```

**Analysis:**

 1. 这个问题要求计算一个数组中连续的部分
 2. 注意一些编程细节即可

