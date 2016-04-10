# 238 Product of Array Except Self

标签（空格分隔）： LeetCode Array

---

**Problem:**
>   Given an array of n integers where n > 1, nums, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].
>
Solve it without division and in O(n).
>
For example, given [1,2,3,4], return [24,12,8,6].

**Analysis:**

 1. 给定一个数组得到没有它自己的乘积的结果，不能用除法，时间复杂度在O(N)。
 2. {1,2,3,4}这个数组，求第三个的乘积时，结果为1*2和4的乘积，所以可以将数组遍历两次，从左向右乘一次，从右向左乘一次。
 3. 中间的关键迭代项目是A[i] = A[i-1]*nums[i-1]和A[i] = A[i+1]*nums[i+1]

**Solution:**
```cpp
std::vector<int> productExceptSelf(std::vector<int>& nums)
	{
		int size = nums.size( );
		std::vector<int> ret(size, 1);

		// 从左往右乘,另一种写法如注释
		// int left = nums[0];
		for (int i = 1; i < size; i++)
		{
			ret[i] = ret[i - 1] * nums[i - 1];
			// ret[i] *= left;
			// left *= nums[i];
		}

		// 从右往左乘
		int right = 1;
		for (int i = size - 1; i >= 0; i--)
		{
			ret[i] *= right;
			right *= nums[i];
		}

		return ret;
	}
```
 
