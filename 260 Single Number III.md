# 260 Single Number III

标签（空格分隔）： LeetCode HashTable Bit_Manipulation

---

**Problem:**
>   Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.
>
For example:
>
Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].

**Analysis:**

 1. 给定一个数组其中由两个数字是单独出现的，求这两个数字。
 2. 哈希表可以做。
 3. 位操作版本，将整个数组做异或得到b^c,其中b和c一定有某一位不同，找出这一位，这一位的0,1把数组分成了两个子数组，即一个数组包含b，一个数组包含c，这样就分别得到了两个数字。

**Solution:**
```cpp
	std::vector<int> singleNumber(std::vector<int>& nums)
	{
		// 先得到整个数组的XOR，实际是两个单独数字的XOR
		int xor1 = 0;
		for (int i = 0; i < nums.size( ); i++)
		{
			xor1 = xor1^nums[i];
		}

		// 找到第一个不同位的位置
		int index = 0;
		for (index = 0; index < 32; index++)
		{
			if ((xor1 >> index) & 1 == 1)
				break;
		}

		// 找出那个特定的数中的一个
		int xor2 = 0;
		for (int i = 0; i < nums.size( ); i++)
		{
			if ((nums[i] >> index) & 1 == 1)
				xor2 = xor2 ^ nums[i];
		}

		std::vector<int> ret = { xor2, xor1 ^ xor2 };
		return ret;
	}
```
 
 **Reference:**
 [【1】比较详细的分析][1]


  [1]: http://fisherlei.blogspot.jp/2015/10/leetcode-single-number-iii-solution.html