## leetcode142_环形链表2

### 原理

> 用set来存储 链表中的各个元素；当遍历的指针发现遍历到遍历过的元素的时候就返回true

```typescript
function detectCycle(head: ListNode | null): ListNode | null {
    var p: ListNode = head;
    var count: Set<ListNode> = new Set();

    while(p){
        if(count.has(p)){
            return p;
        }
        count.add(p);
        p = p.next;
    }

    return null;
};
```

![](https://i.loli.net/2021/05/18/MVgiBnzduQl5vpy.png)


