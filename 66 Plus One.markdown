# 66 Plus One

标签（空格分隔）： LeetCode Array Math

---

**Problem:**
>Given a non-negative number represented as an array of digits, plus one to the number.
The digits are stored such that the most significant digit is at the head of the list.

**Analysis:**

 1. 给一个vector的数，对它进行+1操作。
 2. 考虑进位问题，当进位发生，才需要继续加下去，所以不用进位的时候就可以跳出循环。
 3. 值得注意的是，在最后一位进位时，要在最前面补1。

**Solution:**
```cpp
	std::vector<int> plusOne(std::vector<int>& digits)
	{
		bool first = false;
		std::vector<int> res;
		for (int i = digits.size( ) - 1; i >= 0; i--)
		{
			if (digits[i] + 1 > 9)
			{
				digits[i] = 0;
				if (i == 0)
					first = true;
			}
			else
			{
				digits[i] = digits[i] + 1;
				break;
			}
		}
		
		res = digits;
		if (first == true)
			res.insert(res.begin( ), 1);

		return res;
	}
```

