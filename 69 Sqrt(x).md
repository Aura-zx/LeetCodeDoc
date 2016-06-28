# 69 Sqrt(x)

标签（空格分隔）： LeetCode BinarySearch

---

**Problem:**
>   Implement int sqrt(int x).
>
Compute and return the square root of x.

**Analysis:**

 1. 自己实现开方函数。
 2. 二分法思路。
 3. 值得注意的是其中的某些数字比如2147395599，它的一半的数字依旧大于sqrt(INT_MAX)数，所以在第一次给right赋值的时候判断是否大于该值，若大于则直接赋为该值。
 4. 返回值注意返回mid和right中较小的那个值。

**Solution:**
```cpp
	int mySqrt(int x)
	{
		if (x == 0 || x == 1)
			return x;

		long left = 0;
		long right = x / 2 + 1;
		long mid = 0;
		while (left <= right)
		{
			mid = (right - left) / 2 + left;
			if (mid *mid == x)
				return mid;
			else if (mid*mid < x)
				left = mid + 1;
			else
				right = mid - 1;
		}

		return std::min(right, mid);
	}
```
 
