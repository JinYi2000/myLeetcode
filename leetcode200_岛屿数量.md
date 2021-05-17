# leetcode200_岛屿数量

<img src="https://i.loli.net/2021/05/12/ALNp6doIgzv98R7.png" style="zoom:50%;" />



### 思路：

> 即为图的遍历；
>
> 在遇到1的时候广度优先遍历/深度优先遍历，将遍历到的数字改为0。
>
> 记录下遍历的次数，即为岛屿的数量。



### 深度优先遍历dfs:

```typescript
function numIslands(grid: string[][]): number {
    var res: number = 0;
    var grid1: string[][] = grid;

    var dfs = (i: number,j: number): void => {
        if(i < 0 || i >= grid.length || j < 0 || j >= grid[0].length || parseInt(grid1[i][j]) == 0){
            return;
        } else {
            grid1[i][j] = '0';
            dfs(i-1,j);
            dfs(i,j-1);
            dfs(i+1,j);
            dfs(i,j+1);
        }
        
    }

    for(let i = 0;i < grid.length;i++){
        for(let j = 0;j < grid[0].length;j++){
            if(grid1[i][j] == '1'){
                dfs(i,j);
                res ++ ;
            }
        }
    }

    return res;
};
```

![](https://i.loli.net/2021/05/17/kQAtbHWm27CP8GB.png)











