# 274 H-Index

标签（空格分隔）： LeetCode

---

**Problem:**
>   Given an array of citations (each citation is a non-negative integer) of a researcher, write a function to compute the researcher's h-index.
>
According to the definition of h-index on Wikipedia: "A scientist has index h if h of his/her N papers have at least h citations each, and the other N − h papers have no more than h citations each."
>
For example, given citations = [3, 0, 6, 1, 5], which means the researcher has 5 papers in total and each of them had received 3, 0, 6, 1, 5 citations respectively. Since the researcher has 3 papers with at least 3 citations each and the remaining two with no more than 3 citations each, his h-index is 3.
>
Note: If there are several possible values for h, the maximum one is taken as the h-index.


**Analysis:**

 1. 给一个数字代表各个文章的引用数，求h-index。
 2. 考虑h-index最大值为数组的长度，首先设置h-index为数组的长度，然后对数组排序，遍历数组，当有数组元素小于当前h-index时，h-index减1，否则就跳出循环。

**Solution:**
```cpp
	int hIndex(std::vector<int>& citations)
	{
		std::sort(citations.begin( ), citations.end( ));

		int hindex = citations.size( );
		for (int i = 0; i < citations.size( ); i++)
		{
			if (citations[i] < hindex)
				hindex--;
			else
				break;
		}

		return hindex;
	}
```
 
