# 283 Move Zeros

标签（空格分隔）： LeetCode Array Two-Pointers

---

**Problem:**
>Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

>For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

>Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.


**Solution:**
```cpp
	void moveZeroes(std::vector<int>& nums) {
		if (nums.empty( ))
			return;
		
		// check non-zero number and put them from 0 to cur_pos
		int cur_pos = 0;
		for (size_t i = 0; i < nums.size( ); i++)
		{
			if (nums[i] != 0)
			{
				nums[cur_pos] = nums[i];
				cur_pos++;
			}
		}
		// put 0 in the rest position
		for (size_t i = cur_pos; i < nums.size( ); i++)
			nums[i] = 0;
	}
};
```

**Analysis:**

 1. 题目要求将一个数组中的非零元素顺序不变的移动到数组的前端。
 2. 遍历两次数组：
    第一次将非零数字从数组开端开始放置，并记录当前位置，直到遍历整个数组。
    第二次从记录的当前位置遍历，将剩下的位置变为0。

