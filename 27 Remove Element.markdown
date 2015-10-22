# 27 Remove Element

标签（空格分隔）： LeetCode Arrya TwoPointers

---

**Problem:**
>   Given an array and a value, remove all instances of that value in place and return the new length.
The order of elements can be changed. It doesn't matter what you leave beyond the new length.


**Analysis:**

 1. 将vector中和目标数一样的数字去除。
 2. 没有限制，vector也可以变化。
 3. 直接遍历vector，将不一样的复制下来，一样的不管。


**Solution:**
```cpp
	int removeElement(std::vector<int>& nums, int val)
	{
		int begin = 0;
		for (size_t i = 0; i < nums.size( ); i++)
		{
			if (nums[i] != val)
				nums[begin++] = nums[i];
		}
		return begin;
	}
```

