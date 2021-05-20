## leetcode_136只出现一次的数字

### 原理

> 使用map数据结构记录数组中数字出现的次数；遍历map,如果值为1,则为要找的数字。



```typescript
function singleNumber(nums: number[]): number {
    var count: Map<number,number> = new Map();
    var res: number = -1;

    nums.forEach(el => {
        if(count.has(el)){
            var temp = count.get(el);
            count.set(el,temp+1);
        } else {
            count.set(el,1);
        }
    })

    count.forEach((val,key) => {
        if(val === 1){
            res = key;
        }
    })

    return res;
};
```

 

![](https://i.loli.net/2021/05/21/XMKrqzHmWVIvEeU.png)
