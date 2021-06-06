# Prime Factors
## 質因數分解
> 給定一正整數n, 回傳n的質因數分解結果
```javascript
var generate = function(n){
	var result = [];
	for(var candidate=2; n>1; candidate++){
  	for(; n%candidate==0; n/=candidate) result.push(candidate);
  }
  return result;
}
```