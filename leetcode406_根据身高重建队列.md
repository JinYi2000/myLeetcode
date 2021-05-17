# leetcode406_根据身高重建队列

原理：

> 拿到一个数组；数组中包含了各个人的信息：其身高以及前面大于等于其身高的人的数量
>
> 返回一个包含了所有人顺序的数组
>
> 先根据数对的第一个元素降序排序 --> 先插入的元素都比后插入的元素大，使得第二个元素（身高大于等于）起作用。然后再根据数对的第二个元素将数对插入其位置。
>
> 数对的一般操作：先根据第一个元素正向排序，再根据第二个元素反向排序；或者根据第二个元素反向排序，再根据第一个元素正向排序。

![](https://i.loli.net/2021/05/17/oia7VW3FUIQehbN.png)

```typescript
function reconstructQueue(people: number[][]): number[][] {
    var people0: number[][] = people.sort((a,b) => {
        return a[1] - b[1];
    })

    people0.sort((a,b) => {
        return b[0] - a[0];
    })

    console.log(people0);
    var res: number[][] = [];

    for(let i: number = 0;i < people0.length;i++){
        console.log(res);
        if(res.length < people0[0][1]){
            res.push(people0[i]);
        } else {
            res.splice(people0[i][1],0,people0[i])
        }
    }

    return res;
};
```

![](https://i.loli.net/2021/05/17/jMedY23CyGHR8Ur.png)
