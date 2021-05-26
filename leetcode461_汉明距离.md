## leetcode461_汉明距离.md

主要有一点就是toString()的用法。

比如：8.toString(2)的结果就是1000

里面的参数可以指定要转换到的进制。

```typescript
function hammingDistance(x: number, y: number): number {
    var a: string = x.toString(2);
    var b: string = y.toString(2);

    var maxLen: number = Math.max(a.length,b.length);

    while(a.length < maxLen){
        a = '0' + a;
    }
    while(b.length < maxLen){
        b = '0' + b;
    }

    var res: number = 0;

    for(let i = 0;i < maxLen;i++){
        if(a[i] !== b[i]){
            res++;
        }
    }

    return res;
};
```
