

# leetcode55_跳跃游戏

![](https://i.loli.net/2021/05/14/fsHRvKWIEZQgaoV.png)



### 思路1

> 到达一个位置之后，遍历所有能跳到的位置。（回溯算法）



### 思路2

> 是否能跳到最后一个位置 ——> 前面所有能到的坐标的跳力之和是否能到最后一个坐标



```javascript
var canJump = function(nums) {
    var maxIndex = 0;//能到达的最远距离
    for(let i = 0;i < nums.length;i++){
        if(i <= maxIndex){//该i位置是否可以到达
            maxIndex = Math.max(maxIndex,i + nums[i]);//用了贪心的思想，直接加上能到达的最远距离
        }
        if(maxIndex >= nums.length - 1){
            return true;
        }
    }
    return false;
};
```

![](https://i.loli.net/2021/05/14/CeOs7I2oW5fd8yS.png)





### typescript版本

> 其实就是加上了对变量的类型限制

```typescript
function canJump(nums: number[]): boolean {
    var maxIndex :number = 0;
    for(let i :number = 0;i < nums.length;i++){
        if(i <= maxIndex){
            maxIndex = Math.max(maxIndex,i + nums[i]);
        }
        if(maxIndex >= nums.length - 1){
            return true;
        }
    }
    return false;
};
```


