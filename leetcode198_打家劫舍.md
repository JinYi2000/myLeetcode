## leetcode198_打家劫舍

## 思路

> **动态规划**； 核心要素在于：**两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警**。 	即：要么选当前的屋子，要么选前一间屋子。
>
> 设置一个数组，dp[i]表示的是到第i间屋子时偷到的最大现金数目。
>
> 递推公式:
>
> > Dp[i+1] = Math.max(dp[i],dp[i-1] + nums[i])



```javascript
var rob = function(nums) {
    var len = nums.length;
    if(len == 0) return 0;
    var dp = new Array(len);
    dp[0] = nums[0];
    for(let i = 1;i < len;i++){
        dp[i] = Math.max(dp[i-1],(i-2 >= 0 ? dp[i - 2] + 
        nums[i] : nums[i] ));
    }
    return dp.pop();
};
```



![](https://i.loli.net/2021/05/12/a9xAXNBo2vZiDS4.png)



