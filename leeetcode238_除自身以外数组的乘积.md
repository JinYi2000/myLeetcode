## leeetcode238_除自身以外数组的乘积

### 原理 双指针

> 题目要求不可以使用除法，而且时间复杂度要求O（n）
>
> 可以使用双指针来解。
>
> 设置两个数组，分别记录从左往右以及从右往左的乘积。

```typescript
function productExceptSelf(nums: number[]): number[] {
    //双指针
    var len: number = nums.length;
    var res: number[] = new Array(len);
    var leftMul: number[] = new Array(len);
    var rightMul: number[] = new Array(len);
    leftMul[0] = nums[0];
    rightMul[len-1] = nums[len-1];

    for(let i = 1;i < len;i++){
        leftMul[i] = leftMul[i-1] * nums[i];
    }
    for(let i = len-2;i >= 0;i--){
        rightMul[i] = rightMul[i+1] * nums[i];
    }
    for(let i = 0;i < len;i++){
        if(i === 0){
            res[i] = rightMul[i+1];
        } else if(i === len-1){
            res[i] = leftMul[i-1];
        } else {
            res[i] = leftMul[i-1] * rightMul[i+1];
        }
    }

    return res;
};
```



![](https://i.loli.net/2021/05/24/ksFfVyIU1venSLx.png)
