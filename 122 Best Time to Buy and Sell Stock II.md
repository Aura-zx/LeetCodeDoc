# 122 Best Time to Buy and Sell Stock II

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   
Say you have an array for which the i-th element is the price of a given stock on day i.
>   
Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

**Analysis:**

 1. 给定股票的一组数据，求能多次交易的最佳策略，但是必须在买了之后才可以卖。
 2. 当后一天的钱数大于前一天的钱数的时候做一次交易，遍历数组将后面大于前面的case全部加起来即可。

**Solution:**
```cpp
	int maxProfit(std::vector<int>& prices)
	{
		if (prices.empty( ))
			return 0;

		int min = prices[0];
		int ans = 0;
		for (int i = 1; i < prices.size( ); i++)
		{
			if (prices[i] > min)
			{
				ans += prices[i] - min;
				min = prices[i];
			}
			else
				min = prices[i];
		}

		return ans; 
	}
```
 
