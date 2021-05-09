## leetcode160_相交链表

思路：

> 对两个链表进行遍历，当指针所指位置相等的时候，即为所求节点。
>
> 问题关键：相交节点在两个链表中所处位置不同。



### 暴力法

```javascript
var getIntersectionNode = function(headA, headB) {
    var p1 = headA;
    var p2 = headB;
    var res = null;
    
    while(p1){
        while(p2){
            if(p1 == p2){
                return p1;
            }
            p2 = p2.next;
        }
        p2 = headB;
        p1 = p1.next;
    }
    return res;
}
```

![](https://i.loli.net/2021/05/09/GvbIWURdJKB6VY2.png)



## 哈希表

> 先遍历一个链表，把所有的值存在哈希表中；再遍历另一个链表，看哈希表中是否有相同的值。

```javascript
var getIntersectionNode = function(headA, headB) {
    var p1 = headA;
    var p2 = headB;
    var res = null;
    var count = new Set();
    
    while(p1){
        count.add(p1);
        p1 = p1.next;
    }
    while(p2){
        if(count.has(p2)){
            res = p2;
            break;
        }
        p2 = p2.next;
    }

    return res;
}
```

![](https://i.loli.net/2021/05/09/pvSWNBorAnz4e5k.png)
