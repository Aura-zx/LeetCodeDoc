# 287 Find Duplicate Number

标签（空格分隔）： LeetCode BinarySearch TwoPointers

---

**Problem:**
>   Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.
>
Note:
You must not modify the array (assume the array is read only).
You must use only constant, O(1) extra space.
Your runtime complexity should be less than O(n2).
There is only one duplicate number in the array, but it could be repeated more than once.

**Analysis:**

 1. 找出一个数组中重复的数字，这个数组包含了n+1个数字，每个数字在[1,n]之间。要求，不能修改数组，空间复杂度O(1)，时间复杂度O(N^2)。
 2. 要求是挺多的，但是题目中的n+1个数字都在[1,n]之间，这句话暗示我们可以用数组中的元素作为下标来使用，整个数组可以看做是一个抽象的链表，整个题目转化成了寻找链表中的环的问题，具体的说不是判断有没有环，而是找到环的节点。

**Solution:**
```cpp
	int findDuplicat(std::vector<int>& nums)
	{
		if (nums.size( ) > 1)
		{
			int slow = nums[0];
			int fast = nums[nums[0]];
			while (slow != fast)
			{
				slow = nums[slow];
				fast = nums[nums[fast]];
			}

			fast = 0;
			while (fast != slow)
			{
				fast = nums[fast];
				slow = nums[slow];
			}

			return slow;
		}

		return -1; 
	}
```
 
