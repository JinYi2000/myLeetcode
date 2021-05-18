## leetcode152_乘积最大子数组

### 原理

> 动态规划
>
> 递推公式：**dp[i] = Math.max(dp[i-1] * nums[i],nums[i])**
>
> 问题在于：两个负数乘积也为正数，就会大于原来的数
>
> 解决策略：设置一个数组来存放最小的数；因为负值乘上最小的元素可能会变成最大的元素

```typescript
function maxProduct(nums: number[]): number {
    var dp: number[] = [];
    var dp2: number[] = [];//该数组存放最小的元素
    var res: number = nums[0];

    dp[0] = nums[0];
    dp2[0] = nums[0];    

    for(let i: number = 1;i < nums.length;i++){
        dp[i] = Math.max(dp[i-1] * nums[i],nums[i],dp2[i-1]*nums[i]);
        dp2[i] = Math.min(dp[i-1] * nums[i],nums[i],dp2[i-1]*nums[i]);
    }

    res = Math.max(...dp);
    return res;
};
```



改进之后：

```typescript
function maxProduct(nums: number[]): number {
    var dp: number[] = [];
    var max: number = nums[0];
    var min: number = nums[0];
    var res: number = nums[0];

    for(let i: number = 1;i < nums.length;i++){
        var temp1 = Math.max(max*nums[i],nums[i],min*nums[i]);
        var temp2 = Math.min(max*nums[i],nums[i],min*nums[i]);
        max = temp1;
        min = temp2;
        res = Math.max(max,res);
        //console.log(max,min,res)
    }

    return res;
};
```

### 注意：

> 声明了两个temp变量，因为如果直接对max与min赋值的话，先赋值的那个值就会发生变化，影响后面那个值的计算。




