# 143. 重排链表
给定一个单链表 L：```L0→L1→…→Ln-1→Ln```，  
将其重新排列后变为： ```L0→Ln→L1→Ln-1→L2→Ln-2→…```  

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。  

示例 1:  
```
给定链表 1->2->3->4, 重新排列为 1->4->2->3.
```
示例 2:
```
给定链表 1->2->3->4->5, 重新排列为 1->5->2->4->3.
```

```go
func reorderList(head *ListNode)  {
}
```

## 解题思路
```
// step.1 find mid
// step.2 revert
// step.3 merge
```

## 题解

```go
func reorderList(head *ListNode)  {

    if head == nil || head.Next == nil {
        return
    }

    mid := findMind(head)
    tail := reverse(mid.Next)
    mid.Next = nil

    merge(head, tail)

}

// 快慢指针
func findMind(head *ListNode) *ListNode{
    slow := head
    fast := head.Next

    for slow != nil && fast.Next != nil {
        slow = slow.Next
        fast = fast.Next.Next
    }
    return slow
}

// 反转链表
func reverse(head *ListNode) *ListNode {
    var  pre *ListNode
    current := head

    for current != nil {
        tmp := current.Next
        current.Next = pre
        pre = current
        current = tmp
    }
    return pre
}
// 合并
func merge(head *ListNode, tail *ListNode) {

    dummy := &ListNode {}
    index := 0

    for head != nil && tail != nil {
        if index % 2 == 0 {
            dummy.Next = head
            head = head.Next
        } else {
            dummy.Next = tail
            tail = tail.Next
        }
        dummy = dummy.Next
        index++
    }
    
    if head != nil {
        dummy.Next = head
    }
    if tail != nil {
        dummy.Next = tail
    }
}


```
