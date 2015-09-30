# 169 Majority Element

标签（空格分隔）： LeetCode Divide_and_Conquer Array Bit_Manipulation

---

**Problem:**
>   Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊n/2⌋ times.
    You may assume that the array is non-empty and the majority element always exist in the array.

**Solution:**
```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        //  non-empty and the majority element always exist in the array.
		int maj_index = 0;
		int count = 1;
		for (size_t i = 0; i < nums.size( ); i++)
		{
			if (nums[maj_index] == nums[i])
				count++;
			else
				count--;
			if (count == 0)
			{
				maj_index = i;
				count = 1;				// reset count
			}
		}
		return nums[maj_index];
    }
};
```
**Analysis:**

 1. 求一个长度为n的数组中出现元素出现至少为⌊n/2⌋次的元素，称为主元素
 2. 测试用例保证数组非0且一定会有主元素
 3. 首先想到的方式是二重循环的方法，O(N*N)
 4. 本例使用的方法是O(N)的方法，遍历数组一次即可得到，主要思路是对数组中所有元素计数
    1）默认第一个元素为主元素，主元素的index为`maj_index=0`,当前计数为`count=1`
    2）遍历数组，当前元素和在`maj_index`上的元素一样时，`count++`，否则，`count--`
    3）当`count=0`时，`maj_index`设为当前index，`count`重置为1
    4）遍历数组结束时，返回`maj_index`的元素

**Reference:**
[MajorityElement][1]


  [1]: http://www.geeksforgeeks.org/majority-element/