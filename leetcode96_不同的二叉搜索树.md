## leetcode96_不同的二叉搜索树

### 思路

> 二叉搜索树：比根节点大的节点都在它的右边；比根节点小的节点都在它的左边
>
> 则一个问题可以分解为两个子问题：
>
> 1 - n   n个数字，遍历i作为根节点；
>
> 每次在它的左边有1 - i-1 个节点；在它的右边有 i+1 - n个节点。
>
> 因此可以用动态规划来求解。



```typescript
function numTrees(n: number): number {
    var dp: number[] = new Array(n+1).fill(0);
    dp[0] = 1;
    dp[1] = 1;
    dp[2] = 2
    for(let i = 3;i <= n;i++){
        for(let j = 1;j <= i;j++){
            dp[i] += dp[j-1] * dp[i-j];
        }
    }
    return dp[n];
};
```



![](https://i.loli.net/2021/05/23/aXKemgBIcCJq5uV.png)
