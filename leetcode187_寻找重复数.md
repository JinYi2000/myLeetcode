## leetcode187_寻找重复数

### 原理：快慢指针



```typescript
function findDuplicate(nums: number[]): number {
    var res: number = 0;

    var p1: number = 0;
    var p2: number = 0;

    while(true){
        p1 = nums[p1];
        p2 = nums[p2];
        p2 = nums[p2];
        if(p1 === p2){
            let p3: number= 0;
            while(true){
                p1 = nums[p1];
                p3 = nums[p3];
                if(p1 === p3){
                    res = p1;
                    break;
                }
            }
            break;
        }
    }
    return res;
};
```

![](https://i.loli.net/2021/05/27/9TYvmcJu7HgBFG4.png)
