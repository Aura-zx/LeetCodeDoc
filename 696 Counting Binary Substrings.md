# 696 Count Binary Substrings

标签（空格分隔）： LeetCode

---
**Problem:**
>   Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.
  
> Substrings that occur multiple times are counted the number of times they occur.
>
    Input: "00110011"
    Output: 6
    Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".

    Notice that some of these substrings repeat and are counted the number of times they occur.

    Also, "00110011" is not a valid substring because all the 0's (and 1's) are not grouped together.

**Analysis:**

1. 核心思路：形如“00011111”这样的字符串，相邻连续序列所能组成题目所述的字符串的个数 = 相邻序列中长度最小的那个
比如“00011111”，短的部分是“000”，就有“01”，“0011”，“000111”三种可能
所以可以先计算字符串的相同序列长度，组成一个数组，将这个数组相邻元素最小的依次相加即可。
即“00011111” => [3,5], res = min(3,5) = 3

2. one pass：还是按核心思路进行遍历，维护prev字符的长度，在递增后续新的字符长度时，每递增一次则有一个子串
比如“00011111”的过程：遍历到第一个1时，prev = 3，那么后续每发现一个1则给结果+1



**Solution:**
```javascript
var countBinarySubstrings = function(s) {
    let ans = 0

    let prev = 0
    let cur = 1
    for(let i = 0; i < s.length-1; i++) {
        if(s[i] === s[i+1]) {
            cur++
        } else {
            prev = cur
            cur = 0
            cur++
        }
        if(prev >= cur) {
            console.log(i)
            ans++
        }
    }

    return ans
};
```