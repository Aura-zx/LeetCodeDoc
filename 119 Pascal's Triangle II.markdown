# 119 Pascal's Triangle II

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given an index k, return the kth row of the Pascal's triangle.
>
For example, given k = 3,
Return [1,3,3,1].

**Analysis:**

 1. 求特定行的帕斯卡三角形，注意这里的行和之前的不一样，它的k=3实际上是上题中的第四行。
 2. 首先k=n的行有n+1个数，循环利用数组计算。
 3. 例n=4
> 1 1 1 1 1
  1 2 1 1 1
  1 3 3 1 1
  1 4 6 4 1
 4. 每次计算的时候将前一个替换掉的数字记下来即可。


**Solution:**
```cpp
	std::vector<int> getRow(int rowIndex)
	{
		std::vector<int> res(rowIndex + 1, 1);
		for (int i = 2; i <= rowIndex; i++)
		{
			int pre = 1;
			for (int j = 1; j < i; j++)
			{
				int tmp = res[j];
				res[j] += pre;
				pre = tmp;
			}
		}
		return res;
	}
```
 
