## leetcode78_子集

### 思路

> 回溯算法
>
> 顺序遍历数组，在每个元素的位置可以分为包含该元素以及不包含该元素两种情况。所以是一棵二叉树。
>
> 因为数组中元素各不相同，所以不用考虑元素重复的情况。
>
> 写一个递归函数；在函数的传参中传入遍历元素的次数；当到达最后一层的时候就终止递归。

```typescript
function subsets(nums: number[]): number[][] {
    var level = nums.length;
    var res: number[][] = [];

    var addVal = (val: number,lev: number,arr: number[]) => {
        if(lev === level){
            res.push(arr);
        } else {
            addVal(nums[lev + 1],lev + 1,arr.slice());
            arr.push(val)
            addVal(nums[lev + 1],lev + 1,arr.slice());
        }
    }

    addVal(nums[0],0,[]);

    return res;
};
```

![](https://i.loli.net/2021/05/15/5bFhsylcqZwjABv.png)


