# 88 Merge Sorted Array

标签（空格分隔）： LeetCode TwoPointers

---

**Problem:**
>   Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
>
Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

**Analysis:**

 1. 将两个有序的数组合并在第一个数组中。
 2. key point，从大到小开始比，排列。

**Solution:**
```cpp
		int end = nums1.capacity()-1;
		int i = m - 1;
		int j = n - 1;

		while (i >= 0 && j >= 0)
		{
			if (nums1[i] > nums2[j])
				nums1[end--] = nums1[i--];
			else
				nums1[end--] = nums2[j--];
		}

		while (i >= 0)
			nums1[end--] = nums1[i--];
		while (j >= 0)
			nums1[end--] = nums2[j--];
		if (end > 0)
			std::copy(nums1.begin( ) + end+1, nums1.end( ), nums1.begin( ));
	}
```

