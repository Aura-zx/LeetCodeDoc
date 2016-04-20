# 309 Best Time to Buy and Sell Stock with Cooldown

标签（空格分隔）： LeetCode DP

---

**Problem:**
>   Say you have an array for which the i-th element is the price of a given stock on day i.
>
Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:
>
You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)

**Analysis:**

 1. 卖股票问题，可以选择中间空一天再出售，求整个交易获利最多的值。
 2. 设buy[i]和sell[i]表示当天是买还是卖，显然最大值为sell[n-1]，其中buy[0]=-prices[0]，
 3. sell[i] = max(buy[i-1]+prices[i], sell[i-1]-prices[i-1]+prices[i])
    buy[i]  = max(sell[i-2]-prices[i], buy[i-1]+prices[i-1]-prices[i])

**Solution:**
```cpp
	int maxProfit(std::vector<int>& prices)
	{
		if (prices.size( ) < 2)
			return 0;

		int sz = prices.size( );
		int ret = 0;
		std::vector<int> buy(sz, 0);
		std::vector<int> sell(sz, 0);
		buy[0] = -prices[0];
		for (int i = 1; i < sz; i++)
		{
			// 看着很相似，但主要的区别在于前一天的状态是买还是卖
			// 前一天买的今天卖和前一天不卖今天卖，即cooldown一天
			sell[i] = std::max(buy[i - 1] + prices[i], sell[i - 1] - prices[i - 1] + prices[i]);
			if (ret < sell[i])
				ret = sell[i];
			if (i == 1)
				buy[i] = buy[0] + prices[0] - prices[1];
			else
				buy[i] = std::max(sell[i-2]-prices[i], buy[i-1]+prices[i-1]-prices[i]);
			// 空了一天买和前一天没买今天买
		}

		return ret;
	}
```
**Reference:**
[中文][1]
[英文][2]


  [1]: http://www.cnblogs.com/grandyang/p/4997417.html
  [2]: https://leetcode.com/discuss/81083/an-8ms-c-dp-solution-easy-to-understand