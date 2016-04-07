# 338 Counting Bits

标签（空格分隔）： LeetCode 

---

**Problem:**

> Given a non negative integer number num. For every numbers i in the range 0 ≤ i ≤ num calculate the number of 1's in their binary representation and return them as an array.
>
Example:
For num = 5 you should return [0,1,1,2,1,2].
>
Follow up:
>
It is very easy to come up with a solution with run time O(n*sizeof(integer)). But can you do it in linear time O(n) /possibly in a single pass?
Space complexity should be O(n).
Can you do it like a boss? Do it without using any builtin function like __builtin_popcount in c++ or in any other language.
You should make use of what you have produced already.
Divide the numbers in ranges like [2-3], [4-7], [8-15] and so on. And try to generate new range from previous.
Or does the odd/even status of the number help you in calculating the number of 1s?

**Analysis:**

 1. 题目的意思是输入一个数字`num`将在[0，num]范围内的数的二进制表示中的1的个数作为数组输出。
 2. 和191号问题类似，191号是求某一个数字的二进制表示中的1的个数。
 3. 直观的想法是将范围内的每一个数字用191号的办法处理，得到最后的结果。
 4. 另外一个可以优化的办法是找到1出现次数的规律，见[1]。

**Solution:**
```cpp
int countBit(int num)
	{
		if (num == 0)
			return 0;

		uint32_t res = 0;
		int count = 0;
		for (int i = 0; i < 32; i++)
		{
			res = (1 << i) & num;
			if (res != 0)
				count++;
		}

		return count;
	}

	std::vector<int> countBits(int num)
	{
		std::vector<int> res;
		for (int i = 0; i <= num; i++)
			res.push_back(countBit(i));

		return res;
	}
	
	std::vector<int> countingBits(int num)
	{
		std::vector<int> res(num+1, 0);
		int p = 1;
		int pow = 1;

		for (int i = 1; i <= num; i++)
		{
			if (i == pow)
			{
				res.at(i) = 1;
				pow = pow << 1;
				p = 1;
			}
			else
			{
				res.at(i) = res.at(p)+1;
				p++;
			}
		}

		return res;
	}
```

**Reference:**
[【1】优化的办法][1]


  [1]: http://www.programcreek.com/2015/03/leetcode-counting-bits-java/