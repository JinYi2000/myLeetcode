# leetcode_53最大自序和

![](https://i.loli.net/2021/05/13/54iaEKyzGemF6pj.png)



思路：动态规划

```javascript
var maxSubArray = function(nums) {
    if(nums.length < 1) return 0
    var dp = [];
    dp.push(nums[0]);
    for(let i = 1;i < nums.length;i++){
        dp[i] = Math.max((dp[i-1] + nums[i]),nums[i]);
    }
    return Math.max(...dp);
};
```

![](https://i.loli.net/2021/05/13/12s53KpnjrbwYxA.png)
