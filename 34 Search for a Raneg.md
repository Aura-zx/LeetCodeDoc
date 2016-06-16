# 34 Search for a Raneg

标签（空格分隔）： LeetCode BinarySearch

---

**Problem:**
>   Given a sorted array of integers, find the starting and ending position of a given target value.
>
Your algorithm's runtime complexity must be in the order of O(log n).
>
If the target is not found in the array, return [-1, -1].
>
For example,
Given [5, 7, 7, 8, 8, 10] and target value 8,
return [3, 4].

**Analysis:**

 1. 给一个有序数组，求某个特定元素在里面的index的范围。
 2. 用二分搜索做，对一个数组搜索两次，一搜左边的index，一次搜右边的index。
 3. 注意两次的代码中不一样的地方。

**Solution:**
```cpp
int lsearch(int left, int right, std::vector<int>& nums, int target)
	{
		while (left <= right)
		{
			int mid = (right - left) / 2 + left;
			if (nums[mid] < target)
				left = mid + 1;
			else
				right = mid - 1;
		}
		if (nums[left] != target)
			return -1;

		return left;
	}

	int rsearch(int left, int right, std::vector<int>& nums, int target)
	{
		while (left <= right)
		{
			int mid = (right - left) / 2 + left;
			if (nums[mid] > target)
				right = mid - 1;
			else
				left = mid + 1;
		}
		if (nums[right] != target)
			return -1;

		return right;
	}

	std::vector<int> searchRange(std::vector<int>& nums, int target)
	{
		std::vector<int> res;
		if (nums.empty( ))
			return res;

		int leftindex = lsearch(0, nums.size( ) - 1, nums, target);
		int rightindex = rsearch(0, nums.size( ) - 1, nums, target);

		res.push_back(leftindex);
		res.push_back(rightindex);

		return res;
	}
```