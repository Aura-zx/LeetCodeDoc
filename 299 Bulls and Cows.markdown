# 299 Bulls and Cows

标签（空格分隔）： LeetCode HashTable

---

**Problem:**
>   For example:
>
Secret number:  "1807"
Friend's guess: "7810"
Hint: 1 bull and 3 cows. (The bull is 8, the cows are 0, 1 and 7.)
Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. In the above example, your function should return "1A3B".

**Analysis:**

 1. 题目求两个字符串中，字符值和位置都一样的，称为Bull，字符值正确，但位置不正确的，称为Cow，求这些值
 2. 分两遍搜索，第一次找字符和位置都一样的，第二次找字符一样但位置不正确的。
 3. 注意如‘1122’和‘1222’；‘1122’和‘2211’这些情况，前者为‘3A0B’，后者为‘0A4B’。

**Solution:**
```cpp
		std::string res = "";
		if (secret.size( ) == 0 || guess.size( ) == 0)
			return res;

		std::vector<int> tag(secret.size( ), false);
		std::map<char, int> elem;
		for (int i = 0; i < secret.size( ); i++)
			elem[secret[i]]++;

		int bulls = 0;
		int cows = 0;
		// find the right value && position
		for (int i = 0; i < guess.size( ); i++)
		{
			if (secret[i] == guess[i])
			{
				bulls++;
				elem[secret[i]]--;
				tag[i] = true;
			}
		}

		// find the right value but wrong position
		for (int i = 0; i < guess.size( ); i++)
		{
			if (!tag[i] && elem[guess[i]] > 0)
			{
				cows++;
				elem[guess[i]]--;
			}
		}
		
		res = std::to_string(bulls) + "A" + std::to_string(cows) + "B";

		return res;
```