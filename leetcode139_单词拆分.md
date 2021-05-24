## leetcode139_单词拆分

### 解法1 动态规划

> 问题分解： 0-j 字符是否能被拆分成字典可以分解为 0-i 以及 i-j ,0 <= i <= j 是否能被拆分成字典
>
> 设置 dp[i] 代表 原字符串到i 为止是否能被拆分。



```typescript
function wordBreak(s: string, wordDict: string[]): boolean {
    var dp: boolean[] = new Array(s.length+1).fill(false);
    dp[0] = true;

    for(let i = 0;i <= s.length;i++){
        for(let j = i - 1;j >=0;j--){
            var subWord: string = s.slice(j,i);
            if(wordDict.indexOf(subWord) !== -1 && dp[j]){
                console.log(subWord);
                dp[i] = true;
                break;
            }
        }
    }
    return dp[s.length];
};
```



![](https://i.loli.net/2021/05/24/zRVYJUw4CAy7n3a.png)



### 解法2  bfs解空间树

> 从前往后截取字符，每截取到一个存在于字典中的就截去、重复，直到剩下的字符串为空。

```typescript
function wordBreak(s: string, wordDict: string[]): boolean {
    var res:boolean = false;
    var dfs = (leftStr: string) => {
        console.log(leftStr);
        if(leftStr.length == 0) res = true;
        for(let i = 1;i <= leftStr.length;i++){
            var subStr = leftStr.slice(0,i);
            if(wordDict.indexOf(subStr) !== -1){
                dfs(leftStr.slice(i));
            }
        }
    }   
    dfs(s);
    return res;
};
```

通过了33/42，但是剩下的超出了时间限制。

解空间树中应该存有重复的计算，进行记忆化处理。

```typescript
function wordBreak(s: string, wordDict: string[]): boolean {
    var res:boolean = false;
    var visited: boolean[] = new Array(s.length).fill(false);
    var bfs = (leftStr: string,index: number) => {
        console.log(leftStr);
        if(leftStr.length == 0) res = true;
        for(let i = 1;i <= leftStr.length;i++){
            var subStr = leftStr.slice(0,i);
            if(wordDict.indexOf(subStr) !== -1){
                if(!visited[index+i]){
                    visited[index+i] = true;
                    bfs(leftStr.slice(i),index+i);
                }     
            }
        }
    }   
    bfs(s,0);
    return res;
};
```

在这段代码中：开创了一个数组，用于记录该坐标往后是否有被截取过，大大减少了重复次数。

![](https://i.loli.net/2021/05/24/lzN2PWBTHKe71qb.png)
