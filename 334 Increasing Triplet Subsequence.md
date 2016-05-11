# 334 Increasing Triplet Subsequence

标签（空格分隔）： LeetCode

---

**Problem:**
>   Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.
>
Formally the function should:
    Return true if there exists i, j, k 
    such that arr[i] < arr[j] < arr[k] given 0 ≤ i < j < k ≤ n-1 else return false.
>    
Your algorithm should run in O(n) time complexity and O(1) space complexity.

**Analysis:**

 1. 求一个数组中是否有三个的递增序列。
 2. 设置两个变量x1到目前为止最小值，x2为到目前为止至少有一个值比他小，在确定这两个值以后，只要还有比x2大的就为真，否则为假。
 3. 更新策略是，x1=x2=INT_MAX，当数字比x1小，更新x1；比x2小，更新x2；比x2大，则为真。

**Solution:**
```cpp
	bool increasingTriplet(std::vector<int>& nums)
	{
		if (nums.empty( ))
			return false;

		int x1 = INT_MAX;
		int x2 = INT_MAX;
		for (auto n:nums)
		{
			if (n <= x1)
				x1 = n;
			else if (n <= x2)  // x1 < n < x2
				x2 = n;
			else               // n > x2
				return true;
		}

		return false;
	}
```
 
