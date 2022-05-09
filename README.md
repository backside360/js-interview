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
