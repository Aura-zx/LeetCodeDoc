# 35 Search Insert Position

tags:LeetCode BinarySearch Boundary

---
**Problem:**
>   Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

> You may assume no duplicates in the array.

> Here are few examples.
[1,3,5,6], 5 → 2
[1,3,5,6], 2 → 1
[1,3,5,6], 7 → 4
[1,3,5,6], 0 → 0

**Solution:**
```cpp
int searchInsert(vector<int>& nums, int target) {
    size_t begin = 0;
	size_t end = nums.size() - 1;
	size_t mid = begin + (end - begin) / 2;
	while (1)
	{
	// find target without begin, end
		if (target > nums[mid])
		{
			begin = mid;
			mid = begin + (end - begin) / 2;
		}
		else if (target < nums[mid])
		{
			end = mid;
			mid = begin + (end - begin) / 2;
		}
		else
			return mid;
			
	//can't find target and check begin, end
		if (begin == mid)
			if (target > nums[end])
				return end + 1;
			else if (target > nums[begin] && target < nums[end])
				return end;
			else if (target < nums[begin])
			{
				if (begin == 0)
					return 0;
				else
					return begin - 1;
			}
			else if (target == nums[end])
				return end;
			else if (target == nums[begin])
				return begin;
	}
}
```
**Analysis:**

 1. 问题是查找有序数组中是否有特定数字，有则返回该数字的`index`,没有就返回该数字应该插入的`index`；
 2. 整体思路是二分查找
    第一部分几乎按照标准的迭代式二分查找来做，`mid`赋值时没有+1，-1操作；
 3. 输出插入位置
    第二部分要用到下标信息，因为`mid`没有+1，-1，所以边界条件begin，end是访问不到的，要加一步判断是否等于target.





