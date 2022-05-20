# js-interview
Open library with most popular and common questions/tasks

# Map() polyfill
```javascript
Array.prototype.myMap = function(callbackFn) {
  var arr = [];              
  for (var i = 0; i < this.length; i++) { 
     /* call the callback function for every value of this array and       push the returned value into our resulting array
     */
    arr.push(callbackFn(this[i], i, this));
  }
  return arr;
}
```

# Reduce() polyfill
```javascript
Array.prototype.myReduce= function(callbackFn, initialValue) {
  var accumulator = initialValue;
for (var i = 0; i < this.length; i++) {
    if (accumulator !== undefined) {
      accumulator = callbackFn.call(undefined, accumulator, this[i],   i, this);
    } else {
      accumulator = this[i];
    }
  }
  return accumulator;
}
```

# Filter() polyfill
```javascript
Array.prototype.myFilter = function(callbackFn) {
  var arr = [];     
  for (var i = 0; i < this.length; i++) {
    if (callbackFn.call(this, this[i], i, this)) {
      arr.push(this[i]);
    }
  }
  return arr;
}
```

# Flat() polyfill
```javascript
function flatten(array) {
    const res = []
  
    for (let i = 0; i < array.length; i++) {
      if (Array.isArray(array[i])) {
        const flat = flatten(array[i])
        for (let j = 0; j < flat.length; j++) {
          res.push(flat[j])
        }
      } else {
        res.push(array[i])
      }
    }
  
    return res
  }
```

# Quick sort
```javascript
function quickSort(arr) {
    if (arr.length < 2) return arr;
    let pivot = arr[0];
    const left = [];
    const right = [];
      
    for (let i = 1; i < arr.length; i++) {
      if (pivot > arr[i]) {
        left.push(arr[i]);
      } else {
        right.push(arr[i]);
      }
    }
    return quickSort(left).concat(pivot, quickSort(right));
  }
```

# Brackets
```javascript
function isBalanced(string) {
    const start = '({['
    const end = ']})'
  
    const map = {
      '}': '{',
      ')': '(',
      ']': '['
    }
  
    const queue = []
  
    for (let i = 0; i < string.length; i++) {
      const char = string[i]
  
      if (start.includes(char)) {
        queue.push(char)
      } else if (end.includes(char)) {
        const last = queue.pop()
  
        if (map[char] !== last) {
          return false
        }
      }
    }
  
    return !queue.length
  }
```

# Remove duplicates
```javascript
function removeDupes(str) {
    // const chars = {}
    // const res = []
  
    // for (let i = 0; i < str.length; i++) {
      // if (!chars[str[i]]) {
        // chars[str[i]] = true
        // res.push(str[i])
      // }
    // }
  
    // return res.join('')
  
    return Array.from(new Set(str)).join('')
  }
  
  ```
  
# Maximum subarray
```javascript
var maxSubArray = function(nums) {
    let maxSum = -Infinity
    let previous = 0
    for(let i = 0; i < nums.length; i++){ 
        
        previous = Math.max(nums[i], previous + nums[i])
        
        maxSum = Math.max(previous, maxSum)
        
        
    }
    return maxSum
};
 ```
 
# Move zeroes
```javascript
var moveZeroes = function(nums) {
    let nonZeroIndex = 0;

    for(let i=0; i < nums.length; i++){
        if(nums[i] != 0) {
            nums[nonZeroIndex] = nums[i];
            nonZeroIndex ++;
        }
    }

    for(let i = nonZeroIndex; i < nums.length; i++) {
        nums[i] = 0;
    }
};
 ```
 
 # Merge two sorted lists
 ```javascript
 var mergeTwoLists = function(l1, l2) {
    var mergedHead = { val : -1, next : null },
        crt = mergedHead;
    while(l1 && l2) {
        if(l1.val > l2.val) {
            crt.next = l2;
            l2 = l2.next;
        } else {
            crt.next = l1;
            l1 = l1.next;
        }
        crt = crt.next;
    }
    crt.next = l1 || l2;
    
    return mergedHead.next;
};
 ```

# String to nested object
```javascript
const queryToObject = (query) => {

    return query.split('&').reduce((result, entry) => {
        const [k, v] = entry.split('=')
        const keys = k.split('.')
        let key = 'result', value = `'${v}'`
        for (i = 0; i < keys.length; i++) {
            key += `['${keys[i]}']`
            if (i == keys.length - 1) eval(key + '=' + value)
            else if (!eval(key)) eval(key + '= {}')
        }
        return result
    }, {})

}
```
