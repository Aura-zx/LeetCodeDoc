# 80 Remove Duplicates from Sorted Array II

标签（空格分隔）： LeetCode TwoPointers

---

**Problem:**
>   Follow up for "Remove Duplicates":
What if duplicates are allowed at most twice?
>
For example,
Given sorted array nums = [1,1,1,2,2,3],
>
Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3. It doesn't matter what you leave beyond the new length.

**Analysis:**

 1. 去除有序数组里重复的数字，重复的定义是不大于2个。
 2. 注意代码的简洁性，当数字相同且次数不为2时，次数增加，当为2时忽略。不同的时候则将当前值的后面一个替换成不同的数字，保证了前面的重复只能有2个。

**Solution:**
```cpp
	int removeDuplicates(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return 0;

		int occur = 1;
		int index = 0;
		for (int i = 1; i < nums.size( ); i++)
		{
			if (nums[index] == nums[i])
			{
				if (occur == 2)
					continue;
				occur++;
			}
			else
				occur = 1;

			nums[++index] = nums[i];
		}

		return index + 1;
	}
```
 
