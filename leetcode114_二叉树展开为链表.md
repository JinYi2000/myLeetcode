## leetcode114_二叉树展开为链表

### 思路

> 可以通过递归求解。
>
> 先把左子树展开；把右子树接到左子树链表的尾部；依次递归
>
> 递归函数：把该子树转化为一个链表；返回链表的头节点。

```javascript
const helper = (root) => {       // 将当前子树转成一个单链表
        if (root == null) return null; // 遍历到null节点 返回null节点
        if (root.right) {              // 先生成右子树的单链表
        helper(root.right);
        }
        if (root.left) {               // 如果有左子树，生成单链表然后搬运过去
        const leftFirst = helper(root.left); // 生成单链表，并获取头结点
        let leftLast = leftFirst;    // leftEnd是单链表的尾节点
        while (leftLast.right) {     // 一直找右节点，获取到单链表的尾节点
            leftLast = leftLast.right;
        }
        leftLast.right = root.right; // 尾节点后面接左子树展平后的单链表
        root.right = leftFirst;      // 根节点的right改成leftFirst
        root.left = null;            // root.left置为null
        }
        return root; // 返回出当前子树转成的单链表
    };
    helper(root);  // 原地修改，不用返回
```




