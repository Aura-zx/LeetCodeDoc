# 137 Single Number II

标签（空格分隔）： LeetCode HashTable Bit_Manipulation

---

**Problem:**
>   Given an array of integers, every element appears three times except for one. Find that single one.

**Analysis:**

 1. 同136号问题类似，只不过多次数字的次数变成了三次。
 2. 哈希表的方法一直可以。
 3. 位操作的办法稍微有一些复杂，原理上，出现三次的数字的位的和取余得0。
 4. 上面的方向需要用到二重循环，时间复杂度高，有一个优化的办法，分别设ones，twos和threes为该位的1仅出现了1,2和3次。
 5. 详细解释见代码注释。

**Solution:**
 ```cpp
int singleNumber(std::vector<int>& nums)
	{
		int ones   = 0;
		int twos   = 0;
		int threes = 0;

		for (int i = 0; i < nums.size( ); i++)
		{
			twos |= ones & nums[i];				// &   操作得到ones和当前数字均为1的位数，结果中的1已经表示出现了两次，
												// |   操作得到首次出现的1
			ones ^= nums[i];					// XOR 操作得到首次出现的1，并且将之前的1置0
			threes = ones & twos;               // &   操作得到ones和twos中都出现的1
			
			ones &= ~threes;                    // ~   操作将出现三次的1置0
			twos &= ~threes;					// &   操作将出现三次的1在ones和twos中置0
		}

		return ones;
	}
```

**Reference:**
[【1】掩码变量][1]


  [1]: http://www.acmerblog.com/leetcode-single-number-ii-5394.html