# Leetcode_19 删除链表的倒数第 N 个结点

## 思路：快慢指针

> 让一个节点落后另外一个节点n+1位；当先驱节点到达末尾空指针的时候，后面的节点正好位于要删除的节点的前一个节点；将节点删除之后返回头节点即可。

![](https://i.loli.net/2021/05/14/v9Grikjt2ThE4qw.png)



### 链表中的哑节点(可以避免头节点的特殊处理）

> 在链表头之前添加一个节点，使其next指针指向头节点

```javascript
var removeNthFromEnd = function(head, n) {
    var dummy = new ListNode(0,head);
    var res = dummy.next;
    var p1 = dummy;
    var p2 = dummy;
    var index = n+1;
    while(index){
        p2 = p2.next;
        index--;
    }
    while(p2){
        p2 = p2.next;
        p1 = p1.next;
    }

    p1.next = p1.next.next;
    return dummy.next;
};
```

![](https://i.loli.net/2021/05/14/5mJpCO6A71SWMfT.png)
