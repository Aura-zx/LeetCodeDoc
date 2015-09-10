# 258 Add Digits

标签（空格分隔）： LeetCode Math

---

在此输入正文
**Problem:**
>   Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.
    For example:
    Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.
    
**Solution:**
```cpp
    int addDigits(int num) {
        if (num < 10)
			return num;

		int digit;
		int sum = 0;
		do
		{
			digit = num % 10;
			sum = sum + digit;
			num = num / 10;
			if (sum >= 10 && num == 0)
			{
				num = sum;
				sum = 0;
			}
		} while (num != 0);

		return sum;
    }
```
```cpp
    int addDigits(int num) {
        if (num < 10)
			return num;

        int res;
        res = 1 + (num-1)%9;
        
        return res;
    }
```
**Analysis:**

 1. 该题要求一个正整数的数字根（Digital root），即将整数的各位数字相加，直到这个数字小于10。
 2. 一般的思路是将数字模10相加，再整除10，如此循环，直到最后数字小于10。
 3. 数学的思路是这样：
    dr(abc) = a*100+b*10+c
因为10^k mod 9 = 1所以上式可变为
    dr(abc) = (a*100+b*10+c) mod 9 = a*1+b*1+c (mod 9)
即为我们所求的值。
 4. 因为能被9整除的数字求余为0，所以最后公式做了数学上的处理。
 dr(n) = 1 + (n-1)%9

**Reference:**
[Digital root][1]


  [1]: https://en.wikipedia.org/wiki/Digital_root