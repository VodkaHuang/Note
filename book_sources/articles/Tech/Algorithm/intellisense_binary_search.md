> 二分法查找定式
```javascript
var left = 0;
var right = n;
while (right - left > 1) {
    var mid = left + Math.ceil((right-left)/2);
    if (check(mid))
        left = mid;
    else
        right = mid;
}
return mid;
```