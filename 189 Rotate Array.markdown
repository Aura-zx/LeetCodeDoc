# 189 Rotate Array

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Rotate an array of n elements to the right by k steps.
>
For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

**Analysis:**

 1. 题目求将一个数组看成循环数组，然后进行右移操作。
 2. 简单的想法是开辟另一个数组，将原数组按要求保存进去。
 3. O(1)的方法很巧妙，将数组看成两部分，将两部分分别reverse，再将整个数组reverse得到最后的结果。

**Solution:**
```cpp
	void rotate(std::vector<int>& nums, int k)
	{
		if (nums.empty( ) || k ==0)
			return;
		int n = nums.size( );
		k = k % n;
		if (k != 0)
		{
			ownreverse(nums, 0, n - k - 1);
			ownreverse(nums, n - k, n-1);
			ownreverse(nums, 0, n-1);
		}
	}

	void ownreverse(std::vector<int>& nums, int start, int end)
	{
		while (start < end)
		{
			int tmp = nums[start];
			nums[start] = nums[end];
			nums[end] = tmp;
			start++;
			end--;
		}
	}
```
 
