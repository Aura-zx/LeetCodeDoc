# 121 Best Time to Buy and Sell Stock

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Say you have an array for which the i-th element is the price of a given stock on day i.
>
If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Analysis:**

 1. 给定一只股票和一系列天数的价格，求一次交易的最高收益。
 2. 一次交易指的是前一天买和后一天卖，明白这个问题基本就解决了。
 3. 注意vector空的情况。

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
			if (prices[i] < min)
				min = prices[i];
			else if (prices[i] - min > ans)
				ans = prices[i] - min;
		}

		return ans;
	}
```
 
