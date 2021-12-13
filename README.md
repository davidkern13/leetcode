# leetcode

Two Sum

```Javascript

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */

const twoSum = function(nums, target) {
    const hash = {};
    const ln = nums.length;
    for (let i = 0; i < ln; i++) {
        const diff = target - nums[i];
        if (diff in hash) {
          return [hash[diff], i];
        }
        hash[nums[i]] = i;
    }  
    return hash;
};

```

fibonacci-number

```Javascript

/**
 * @param {number} n
 * @return {number}
 */
const fib = function(n) {
    if(!n) return 0;
    if(n <= 2) return 1;
    return fib(n-1) + fib(n-2);
};

```

Binary Search

```Javascript

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const search = function(nums, target) {
    let left = 0, right = nums.length - 1;
    while(left <= right){
        let mid = ~~((right + left) / 2);
        if(nums[mid] === target) return mid;
        if(nums[mid] < target){
           left = mid + 1;
        }else{
           right = mid - 1;
        }
    }
    
    return -1
};

```
Minimum Value to Get Positive Step by Step Sum

```Javascript

/**
 * @param {number[]} nums
 * @return {number}
 */


var minStartValue = function(nums) {
    let sum = 0;
    let total = 0;
    let total_temp = 0;
    for(let num of nums){
        sum += num;
        if(sum < 1){
            total = sum;
            if(total_temp > sum){
               total_temp = sum;
            }
        }
    }
    return (total_temp * -1) + 1;
};

```

Palindrome Number

```Javascript

/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(num) {
    const string = num + "";
    let ln = string.length - 1;
    for(let i = 0, k = ln; i < ln;){
        if(string.charAt(i++) != string.charAt(k--)){
           return false;
        }
    }
    return true;
};

```

Remove Duplicates from Sorted Array

```Javascript

/**
 * @param {number[]} nums
 * @return {number}
 */


var removeDuplicates = function(nums) {
    let length = nums.length;
    if(length == 0) return 0;
    let k = 0;
    for(let i = 1; i < length; i++){
        if(nums[i] != nums[k]){
           nums[++k] = nums[i];
        }
    }
    return k+1;
};

```

Remove Element

```Javascript

/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */

var removeElement = function(nums, val) {
    let k = 0;
    for(let i = 0; i < nums.length; i++){
       if(nums[i] != val){
        nums[k] = nums[i]; ++k;
       }
    }
    return k;
};

```

Search Insert Position

```Javascript

/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */

var searchInsert = function(nums, target) {
    let i = 0;
    let count = 0;
    let length = nums.length;
    
    while(i <= length){
        if(nums[i] < target){
           count++;
        }
        i++;
    }
    return count;
};

```

Best Time to Buy and Sell Stock

```Javascript

/**
 * @param {number[]} prices
 * @return {number}
 */


var maxProfit = function(prices) {

    let profit = 0;
    let costPrice = prices[0];
    let length = prices.length;
    
    for(let i = 1; i<= length; i++){
        if(profit < prices[i] - costPrice){
           profit = prices[i] - costPrice;
        }
        
        if(costPrice > prices[i]){
           costPrice = prices[i]
        }
    }
     
    return profit;
};

```
