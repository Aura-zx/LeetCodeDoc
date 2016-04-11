# 319 Bulb Switcher

标签（空格分隔）： LeetCode Math

---

**Problem:**
>   There are n bulbs that are initially off. You first turn on all the bulbs. Then, you turn off every second bulb. On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb. Find how many bulbs are on after n rounds.
>
Example:
>
Given n = 3. 
>
    At first, the three bulbs are [off, off, off].
    After first round, the three bulbs are [on, on, on].
    After second round, the three bulbs are [on, off, on].
    After third round, the three bulbs are [on, off, off]. 
>
So you should return 1, because there is only one bulb is on.

**Analysis:**

 1. 模拟类的题，一开始的灯是全暗的，第一轮全亮，后面没一轮将能整除该轮次的序号的灯的状态改变，求最后几盏灯亮着。
 2. 数学语言来讲就是求因子个数为奇数的数的个数。
 3. 因子个数为奇数的数，必然有两个因子是相同的，所以这样的数就是完全平方数，所以就是求完全平方数的个数。
 4. 不大于n的完全平方数的个数为floor(sqrt(n))。

**Solution:**
```cpp
	int bulbSwitcher(int n)
	{
		return sqrt(n);
	}
```
 
