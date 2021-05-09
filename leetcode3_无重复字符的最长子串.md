## leetcode3_无重复字符的最长子串



思路：

> 初始化：左右指针位于0，变量maxLen记录最大的长度，set数据结构count记录已有字符串中的字符。
>
> 过程：将右指针不断右移，当左右指针之间的字符出现重复的时候停止；将此时的字符长度与已有长度进行比较；右指针右移一格；左指针左移，直到将之前重复的字符排除出字符串；以此类推，直到右指针到达字符串末尾。
>
> 原理：对字符串进行遍历，以每个字符为起点，依次求出以这个字符为起点的不包含重复字符的字符串。

```javascript
var lengthOfLongestSubstring = function(s) {
    if(!s) return 0;
    if(s.length == 1) return 1;
    
    var maxLen = 0;
    var l = 0;
    var r = 0;
    var count = new Set();
    count.add(s[0]);

    while(r < s.length - 1){
        r++;
        while(count.has(s[r]) && l < r){
            count.delete(s[l]);
            l++;
        }
        count.add(s[r]);
        console.log(count.size);
        maxLen = count.size > maxLen ? count.size : maxLen;
    }
    return maxLen;
};
```

![](https://i.loli.net/2021/05/09/fyw6TecHuGJKAVr.png)


### 改进之后

```javascript
var lengthOfLongestSubstring = function(s) {
    if(!s) return 0;
    if(s.length == 1) return 1;
    
    var maxLen = 0;
    var l = 0;
    var r = 0;
    var count = new Set();
    count.add(s[0]);

    for(let i = 0;i < s.length;i++){
        if(i !== 0){
            count.delete(s[i-1]);
        }
        while(!count.has(s[r+1]) && r < s.length - 1){
            count.add(s[r+1]);
            r++;
        }
        maxLen = Math.max(maxLen,r - i + 1);
    }
    return maxLen;
};
```



![](https://i.loli.net/2021/05/09/j9YtOSsflU7ZFgx.png)

