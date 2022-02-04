# leetcode

<a href="#Two-Sum">Two-Sum<a/> </br>
<a href="#Fibonacci-Number">Fibonacci-Number<a/> </br>
<a href="#Binary-Search">Binary-Search<a/> </br>
<a href="#MV">Minimum Value to Get Positive Step by Step Sum<a/> </br>
<a href="#Palindrome-Number">Palindrome-Number<a/> </br>
<a href="#Remove-Duplicates-from-Sorted-Array">Remove-Duplicates-from-Sorted-Array<a/> </br>
<a href="#Remove-Element">Remove-Element<a/> </br>
<a href="#Search-Insert-Position">Search-Insert-Position<a/> </br>
<a href="#Best-Time-to-Buy">Best-Time-to-Buy<a/> </br>
<a href="#Binary-Search">Binary-Search<a/> </br>
<a href="#Binary-Search">Binary-Search<a/> </br>
<a href="#Binary-Search">Binary-Search<a/> </br>

<section id="Two-Sum">
<h3>Two Sum</h3>
</section>

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

<section id="Fibonacci-Number">
<h3>Fibonacci-Number</h3>
</section>


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

<section id="Binary-Search">
<h3>Binary Search</h3>
</section>

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

<section id="MV">
<h3>Minimum Value to Get Positive Step by Step Sum</h3>
</section>

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

<section id="Palindrome-Number">
<h3>Palindrome Number</h3>
</section>

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

<section id="Remove-Duplicates-from-Sorted-Array">
<h3>Remove Duplicates from Sorted Array</h3>
</section>

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

<section id="Remove-Element">
<h3>Remove-Element</h3>
</section>

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

###  Search Insert Position

<section id="Search-Insert-Position">
<h3>Search Insert Position</h3>
</section>

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

<section id="Best-Time-to-Buy">
<h3>Best Time to Buy and Sell Stock</h3>
</section>

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

###  Implement strStr()

```Javascript

/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */

var strStr = function(haystack, needle) {
    let haystackLength = haystack.length;
    let needleLength = needle.length;

    if(haystackLength < needleLength) return -1;

    for(let i = 0; i <= haystackLength-needleLength; i++){
        if(haystack.substring(i, i+needleLength) == (needle)){
           return i;
        }
    }
    return -1;
};

```

###  Maximum Ice Cream Bars

```Javascript

var maxIceCream = function(costs, coins) {
    let output = 0;
    costs = costs.sort((a,b) => a - b);
    costs.forEach( (icecream) => {
        if(coins >= icecream){
           output += 1;
           coins -= icecream;
        }
    });
    return output;
};

```



###  Minimum Absolute Difference

```Javascript

const diff = (a, b) => {
    return (a > b) ? (a - b) : (b - a);
}

var minimumAbsDifference = function(arr) {
    
    let array = [];
    let temp = Infinity;
    
    arr = arr.sort((a,b) => a - b);
    
    for(let i = 0; i < arr.length; i++){
        
        let diff_v = diff(arr[i], arr[i+1]);
        
        if(temp == diff_v){
            array.push([arr[i], arr[i+1]]);
        }else if(diff_v < temp){
            array = [];
            array.push([arr[i], arr[i+1]]);
            temp = diff_v;
        }
    }
    return array;
};

```

###  LRU Cache

```Javascript

/**
 * @param {number} capacity
 */
var LRUCache = function(capacity) {
    
    
   this.map = new Map();
   this.capacity = capacity;
    
};

/** 
 * @param {number} key
 * @return {number}
 */

LRUCache.prototype.get = function(key) {
    if(!this.map.has(key)){
        return -1;
    } 
    let value = this.map.get(key);
    this.map.delete(key);
    this.map.set(key, value);
    return value;
};

/** 
 * @param {number} key 
 * @param {number} value
 * @return {void}
 */
LRUCache.prototype.put = function(key, value) {
    if(this.map.get(key)){
       this.map.delete(key);
       this.map.set(key, value);
    }
    this.map.set(key, value);
    if(this.map.size > this.capacity){
        this.map.delete(this.map.keys().next().value);
    }
};

/** 
 * Your LRUCache object will be instantiated and called as such:
 * var obj = new LRUCache(capacity)
 * var param_1 = obj.get(key)
 * obj.put(key,value)
 */
 
 ```
 
 ### Maximum Depth of Binary Tree
 
 ```Javascript
 
 let maxDepth = function(node) {
    let data = mDepth(node);
    return data;
};

let mDepth = (node) => {
    if(node == null) {
        return null;
    }
    let left = mDepth(node.left) + 1;
    let right = mDepth(node.right) + 1;
    
    return right > left ? right : left;
}

```
