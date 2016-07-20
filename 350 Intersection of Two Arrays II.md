# 350 Intersection of Two Arrays II

标签（空格分隔）： LeetCode BinarySearch HashTable

---

**Problem:**
>   Given two arrays, write a function to compute their intersection.
>
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].
>
Note:
Each element in the result should appear as many times as it shows in both arrays.
The result can be in any order.
Follow up:
What if the given array is already sorted? How would you optimize your algorithm?
What if nums1's size is small compared to nums2's size? Which algorithm is better?
What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

**Analysis:**

 1. 和1中明显的不同是最后的结果中出现的数字次数和两次数组中出现的次数一样。
 2. 既然要和两边出现的次数一样多，首先考虑短的那个数组，存入哈希表，然后遍历长的数组，遇到相同的次数-1并存入结果。

**Solution:**
```cpp
	std::vector<int> intersect(std::vector<int>& nums1, std::vector<int>& nums2)
	{
		std::map<int, int> m1;
		std::vector<int> res;

		std::vector<int> st;
		std::vector<int> lar;
		if (nums1.size( ) < nums2.size( ))
		{
			st = nums1;
			lar = nums2;
		}
		else
		{
			st = nums2;
			lar = nums1;
		}

		for (auto i : st)
		{
			if (m1.find(i) == m1.end( ))
				m1[i] = 1;
			else
				m1[i]++;
		}

		for (auto i :lar)
		{
			if (m1[i] > 0)
			{
				res.push_back(i);
				m1[i]--;
			}
		}

		return res;
	}
```
 
