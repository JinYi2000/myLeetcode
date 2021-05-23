## leetcode39_组合总和

### 原理

> 第一反应就是用回溯法 + 剪枝
>
> 每个元素可以无限重复次被选取



### 初版漏洞代码

```typescript
function combinationSum(candidates: number[], target: number): number[][] {
    var res: number[][] = [];

    var traverse = (ans: number[],index: number,total: number) => {
        if(index === candidates.length){
            if(total === target){
                res.push(ans);
            }
        } else {
            if(total <= target ){
                traverse([...ans,candidates[index]],index + 1,(total + candidates[index]));
                traverse([...ans],index + 1,(total));
            }
        }
    }

    traverse([],0,0);

    return res;
};
```

忘记考虑**每个元素可以无限重复次被选取**

### 优化之后

```typescript
function combinationSum(candidates: number[], target: number): number[][] {
    var res: number[][] = [];

    var traverse = (ans: number[],total: number) => {
        if(total >= target){
            if(total === target){
                res.push(ans);
            }
        } else {
                for(let i = 0;i < candidates.length;i++){
                    traverse([...ans,candidates[i]],(total + candidates[i]));
                }  
        }
    }

    traverse([],0);

    return res;
};
//[[2,2,3],[2,3,2],[3,2,2],[7]]
```

解集重复，报错。



可以做一个控制：只允许加上比自己大的元素，以保证解集元素的单调性。

得到了正确答案。



最终解

```typescript
function combinationSum(candidates: number[], target: number): number[][] {
    var res: number[][] = [];

    var traverse = (ans: number[],total: number,index: number) => {
        if(total >= target){
            if(total === target){
                res.push(ans);
            }
        } else {
                for(let i = index;i < candidates.length;i++){
                    traverse([...ans,candidates[i]],(total + candidates[i]),i);
                }  
        }
    }
    
    traverse([],0,0);
    return res;
};
```

![](https://i.loli.net/2021/05/23/NlAZEhsrc7wz1Sv.png)

