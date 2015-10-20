# 202 Happy Number

标签（空格分隔）： LeetCode HashTable Set

---

**Problem:**
>   Write an algorithm to determine if a number is "happy".
>   
A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.
>
Example: 19 is a happy number
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1

**Analysis:**

 1. 题目要求一个数是否为HappyNumber，定义是这个数在分解之后，每一位求平方和，如果结果可以得到1，则为
 Happy Number，若一直循环都不能得到1，则不是Happy Number。
 2. 问题的关键在于如何判断一直循环都不能得到1。显然用次数来判断是不正确的，我们可以通过判断是否有环来确定是否会无限进行下去。
 3. 具体思路就是结合Set结构，将每一次运算的结果存入其中，同时在每次结果时判断，若有重复则返回`false`，当值为1时跳出循环，返回`true`。
 
**Solution:**
```cpp
bool isHappy(int n)
	{
		if (n < 0)
			return false;

		std::set<int> cycle;
		while (n != 1)
		{
			if (cycle.count(n))
				return false;
			else
				cycle.insert(n);

			int sum = 0;
			while (n > 0)
			{
				sum += (n % 10)*(n % 10);
				n = n / 10;
			}
			n = sum;
		}
		return true;
```

