# 7 Reverse Integer

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   Reverse digits of an integer.
>
Example1: x = 123, return 321
Example2: x = -123, return -321

**Analysis:**

 1. 题目求一个整数的逆序。
 2. 可以用`res = res*10 + x/10`式子求解。
 3. 注意溢出用`res > INT_MAX/10`和`res < INT_MIN/10`判断。

**Solution:**
```cpp
	int reverse(int x)
	{		
		int  res = 0;
		while (x != 0){
			if (res > INT_MAX / 10 || res < INT_MIN / 10)
				return 0;
			res = res * 10 + x % 10;
			x = x / 10;
		}
		return res;
	}
```

