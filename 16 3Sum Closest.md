# 16 3Sum Closest

标签（空格分隔）： LeetCode TwoPointers

---

**Problem:**
>   Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.
>
    For example, given array S = {-1 2 1 -4}, and target = 1.
    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).


**Analysis:**

 1. 给一个数组和目标数字，求数组中哪三个数的和与目标数字只差最小。
 2. 和3Sum解决思路一样，维护一个局部diff和最小mindiff，当diff小于mindiff时，更新mindiff，最后返回target-mindiff

**Solution:**
```cpp
int threeSumClosest(std::vector<int>& nums, int target)
	{
		if (nums.size( ) < 3)
			return INT_MAX;
		std::sort(nums.begin( ), nums.end( ));
		int minDiff = INT_MAX;
		for (int i = 0; i < nums.size( ) - 2; i++)
		{
			int left = i + 1;
			int right = nums.size( ) - 1;
			while (left < right)
			{
				int diff = nums[i] + nums[left] + nums[right] - target;
				if (abs(diff) < abs(minDiff))
					minDiff = diff;
				if (diff == 0)
					break;
				else if (diff < 0)
					left++;
				else
					right--;
			}
		}

		return target + minDiff;
	}
```
 
