### 632 Smallest Range Covering Elements from K Lists

### 问题
> You have k lists of sorted integers in ascending order. Find the smallest range that includes at least one number from each of the k lists.

> We define the range [a,b] is smaller than range [c,d] if b-a < d-c or a < c if b-a == d-c.

    Input: [[4,10,15,24,26], [0,9,12,20], [5,18,22,30]]
    Output: [20,24]
    Explanation: 
    List 1: [4, 10, 15, 24,26], 24 is in range [20,24].
    List 2: [0, 9, 12, 20], 20 is in range [20,24].
    List 3: [5, 18, 22, 30], 22 is in range [20,24].


### 解题思路

设一共有 n 个数组，每次循环访问每个数组的一个元素得到 k1...kn 个元素，
1. 计算 n 个元素中的最大区间，也就是 [mix(k1...kn), max(k1...kn)]
2. 当这个区间的长度变小，替换它
3. 每次迭代只替换 k1...kn 数组中最小的那个值
4. 当最小值的元素已经是它所在数组的最后一个元素就停止，得到最终的结果

### 代码

```javascript
/**
 * @param {number[][]} nums
 * @return {number[]}
 */
var smallestRange = function(nums) {
    let numsIndex = [] // 记录数组当前访问到的元素下标
    let totalNums = 0 // 所有数组长度的和
    let allMinNumber = Number.MAX_SAFE_INTEGER // 最终区间的左值
    let allMaxNumber = Number.MIN_SAFE_INTEGER // 最终区间的右值
    let currentMinNumberListIndex = 0 // 当前最小元素所在数组的数组下标，即nums[currentMinNumberListIndex]

    // 初始化过程
    for(let i = 0; i <nums.length; i++){
        numsIndex.push(0)
        totalNums+=nums[i].length
        if(nums[i][0] > allMaxNumber) {
            allMaxNumber = nums[i][0]
        }
        if(nums[i][0] < allMinNumber) {
            allMinNumber = nums[i][0]
            currentMinNumberListIndex = i
        }
    }

    // 获得最小元素后，将会访问这个数组的下一个元素
    numsIndex[currentMinNumberListIndex] += 1

    for(let i = 0; i < totalNums; i++) {
        if(numsIndex[currentMinNumberListIndex] === nums[currentMinNumberListIndex].length) {
            break
        }
        let currentMinNumber = Number.MAX_SAFE_INTEGER
        let currentMaxNumber = Number.MIN_SAFE_INTEGER
        for(let j = 0; j < nums.length; j++) {
            let currentNumber = nums[j][numsIndex[j]]
            if(currentNumber < currentMinNumber) {
                currentMinNumber = currentNumber
                currentMinNumberListIndex = j
            }
            if(currentNumber > currentMaxNumber) {
                currentMaxNumber = currentNumber
            }
        }
        if(currentMaxNumber-currentMinNumber < allMaxNumber-allMinNumber) {
            allMinNumber = currentMinNumber
            allMaxNumber = currentMaxNumber
        }
        numsIndex[currentMinNumberListIndex] += 1
    }
    
    return [allMinNumber, allMaxNumber]
};
```