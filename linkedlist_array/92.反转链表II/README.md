# 92. 反转链表 II
反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。  

说明:  
1 ≤ m ≤ n ≤ 链表长度。  

示例:  
```
输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL
```

```go
func reverseBetween(head *ListNode, m int, n int) *ListNode {
}
```

## 解题思路
二刷 没做出来，对指针操作不熟

## 题解

```go
func reverseBetween(head *ListNode, m int, n int) *ListNode {
    dummy := &ListNode{
        Next: head,
    }

    head = dummy
    for i := 1; i < m; i++ {
        head = head.Next
    }
    
    pre := head
    mNode := head.Next
    nNode := mNode
    postNode := nNode.Next

    for i := m; i < n; i++ {
        
        if postNode == nil {
            return nil
        }
        tmp := postNode.Next
        postNode.Next = nNode
        nNode = postNode
        postNode = tmp
    }
    mNode.Next = postNode
    pre.Next = nNode

    return dummy.Next

}
```
