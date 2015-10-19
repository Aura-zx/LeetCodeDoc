# 292 Nim Game

标签（空格分隔）： LeetCode 

---

**Problem:**
>   You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

>   Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.
    
>   For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.

>   Hint:
    If there are 5 stones in the heap, could you figure out a way to remove the stones such that you will always be the winner?

**Analysis:**

 1. 有一堆石子，每人每次各拿1-3个，谁最后能拿完石子谁赢，你先拿。
 2. 结合题目和提示，4个的情况是必输的，5(4+1)个的情况则是必赢的，同理可得6(4+2),7(4+3)个的情况也都是必赢的。
 3. 解决方法非常简单，判断`n`值是否为4的倍数即可，是则必输，否则必胜。

**Solution:**
```cpp
	bool canWinNim(int n)
	{
		if (n <= 0)
			return false;
		if (n % 4 == 0)
			return false;
		else
			return true;
	}
```
