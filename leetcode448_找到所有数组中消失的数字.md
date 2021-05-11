## leetcode448_找到所有数组中消失的数字

### 思路1

> 先排序；寻找不在遍历顺序中的数字。



### 思路2
> 既然有元素缺失，那必然有其他的元素重复；将所有出现过的元素记录在一个set中；将res数组中去除掉出现在set中过的元素。


```javascript
var findDisappearedNumbers = function(nums) {
    var len = nums.length;
    var res = [];
    for(let i = 1;i <= len;i++){
        res[i-1] = i;
    }
    var count = new Set();

    nums.forEach(el => {
        count.add(el);
    });

    for(let item of count){
        var index = res.indexOf(item);
        if( index !== -1){
            res.splice(index,1);
        }
    }
    
    return res;
};
```

![](https://i.loli.net/2021/05/12/A4bCfKLxXuizWnT.png)
