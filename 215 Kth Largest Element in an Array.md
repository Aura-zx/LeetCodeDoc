# 215 Kth Largest Element in an Array

标签（空格分隔）： LeetCode Heap Divide_and_Conquer

---

**Problem:**
>   Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
>
For example,
Given [3,2,1,5,6,4] and k = 2, return 5.

**Analysis:**

 1. 求一个无序数组中的第k个大的数字。
 2. 排序。
 3. 最小堆，将所有的数字放入最小堆，最后取出k-1个数字，此时堆顶的数字就是结果。
 4. 最大堆，这个方法是错的，wrong case [2,1] k = 2，结果应该是1，最大堆方法总是2。
 5. 快速选择，O(N) on average.

**Solution:**
```cpp
class Solution_215
{
private:
	void swap(std::vector<int>& nums, int i, int j)
	{
		int temp = nums[i];
		nums[i] = nums[j];
		nums[j] = temp;
	}

	int QuickSelect(std::vector<int>& nums, int k, int start, int end)
	{
		int pivot = nums[end];

		int left = start;
		int right = end;

		while (true) {

			while (nums[left] < pivot && left < right) {
				left++;
			}

			while (nums[right] >= pivot && right > left) {
				right--;
			}

			if (left == right) {
				break;
			}

			swap(nums, left, right);
		}

		swap(nums, left, end);

		if (k == left + 1) {
			return pivot;
		}
		else if (k < left + 1) {
			return QuickSelect(nums, k, start, left - 1);
		}
		else {
			return QuickSelect(nums, k, left + 1, end);
		}
	}

public:
	int findkthLargest(std::vector<int>& nums, int k)
	{
		return QuickSelect(nums, nums.size( ) - k+1, 0, nums.size( ) - 1);
	}
};
```


**Reference:**
[多种方法介绍][1]
[耶鲁QuickSelect介绍][2]
 


  [1]: http://www.geeksforgeeks.org/kth-smallestlargest-element-unsorted-array/
  [2]: http://www.cs.yale.edu/homes/aspnes/pinewiki/QuickSelect.html