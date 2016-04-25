# 75 Sort Colors

标签（空格分隔）： LeetCode Sort TwoPointers

---

**Problem:**
>   Given an array with n objects colored red, white or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white and blue.
>
Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

**Analysis:**

 1. 题目稍微有些难懂，实际上就是把一个只包含0,1,2的数组进行排序，要求O（N）
 2. 看到O（N）基本可以确定用计数排序（counting sort），思路是将有几个0,1,2记录在一个count数组中，遍历这个数组，将不为0的计数的元素放入原数组即可。
 3. 双指针的思路是先初始化left和right指针，分别表示可以插入0和2当前的位置，另外有一个当前指针cur。cur为0时，和left交换元素，为2时和right交换元素，为1时自加。

 
**Solution:**
```cpp
	void sortColors(std::vector<int>& nums)
	{
		if (nums.empty( ) || nums.size( ) < 2)
			return;

		std::vector<int> count(3);
		for (int i = 0; i < nums.size( ); i++)
			count[nums[i]]++;

		int j = 0;
		int k = 0;
		while (j <= 2)
		{
			if (count[j] != 0)
			{
				nums[k++] = j;
				count[j]--;
			}
			else
				j++;
		}
	}
```
 
