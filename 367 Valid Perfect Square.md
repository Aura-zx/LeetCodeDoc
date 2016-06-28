# 367 Valid Perfect Square

标签（空格分隔）： LeetCode BinarySearch Math

---

**Problem:**
>   Given a positive integer num, write a function which returns True if num is a perfect square else False.
>
Note: Do not use any built-in library function such as sqrt.
>   
Example 1:
Input: 16
Returns: True
>
Example 2:
Input: 14
Returns: False

**Analysis:**

 1. 判断一个数是否为完全平方数。
 2. 用二分法可解。
 3. 需要注意几个细节，右节点选择一定要是num/2+1，对应的bad case 是4，left **<=** right，等于号一定要有，对应的bad case 是9。

**Solution:**
```cpp
	bool isPerfectSquare(int num)
	{
		if (num == 0 || num == 1)
			return true;

		long long left = 0;
		long long right = num / 2 + 1;

		while (left <= right)
		{
			long long mid = (right - left) / 2 + left;
			if (mid*mid == num)
				return true;
			else if (mid*mid > num)
				right = mid - 1;
			else
				left = mid + 1;
		}

		return false;
	}
```
 
