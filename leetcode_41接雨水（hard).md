# leetcode_41接雨水

<img src="https://i.loli.net/2021/05/12/znRKCrF5AuQ4gNe.png" style="zoom:50%;" />

### 思路1:动态规划

> 在位置i所接雨水的数量 = 左边/右边柱子的最大高度 - 位置i柱子的高度
>
> 实现原理： 设置数组 maxLeft 记录位置i处左侧最大的柱子高度；设置数组 maxRight 记录位置i处右侧最大的柱子高度；数组maxheight记录位置i处左边/右边柱子的最大高度；
>
> Maxheight - nums 得到res.

```javascript
var trap = function(height) {
    var len = height.length;
    var leftMax = new Array(len);
    var rightMax = new Array(len);
    var maxHeight = new Array(len);
    var res = new Array(len);

    res[0] = 0;
    res[len - 1] = 0;

    leftMax[0] = 0;
    rightMax[len - 1] = 0;

    for(let i = 1;i < len;i++){
        leftMax[i] = Math.max(leftMax[i - 1],height[i - 1]);
    };
    for(let i = len - 2;i >= 0;i--){
        rightMax[i] = Math.max(rightMax[i + 1],height[i + 1]);
    };

    for(let i = 0;i < len;i++){
        maxHeight[i] = Math.min(leftMax[i],rightMax[i]);
    }

    for(let i = 1;i < len - 1;i++){
        res[i] = maxHeight[i] - height[i] > 0 ? maxHeight[i] - height[i] : 0;
    }

    return res.reduce((total,val) => {
        return total += val;
    })
};
```

<img src="https://i.loli.net/2021/05/12/XtbKFgHmOaJhcTI.png" style="zoom:50%;" />



#### 另：js中的reduce方法

> 对数组中的每个元素执行一个由您提供的**reducer**函数(升序执行)，将其结果汇总为单个返回值。
>
> **reducer** 函数接收4个参数:
>
> 1. Accumulator (acc) (累计器)
> 2. Current Value (cur) (当前值)
> 3. Current Index (idx) (当前索引)
> 4. Source Array (src) (源数组)
>
> 您的 **reducer** 函数的返回值分配给累计器，该返回值在数组的每个迭代中被记住，并最后成为最终的单个结果值。








