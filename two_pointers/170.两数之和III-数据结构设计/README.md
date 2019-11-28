# 170. 两数之和 III - 数据结构设计
设计并实现一个 TwoSum 的类，使该类需要支持 add 和 find 的操作。  

add 操作 -  对内部数据结构增加一个数。  
find 操作 - 寻找内部数据结构中是否存在一对整数，使得两数之和与给定的数相等。  

示例 1:
```
add(1); add(3); add(5);
find(4) -> true
find(7) -> false
```

示例 2:
```
add(3); add(1); add(2);
find(3) -> true
find(6) -> false
```
```go
```

## 解题思路

## 题解

```go
type TwoSum struct {
    store map[int]int
}

/** Initialize your data structure here. */
func Constructor() TwoSum {
    return TwoSum{
        store: make(map[int]int,0),
    }
}

/** Add the number to an internal data structure.. */
func (this *TwoSum) Add(number int)  {
    
    v,_ := this.store[number]
    v++
    this.store[number] = v
}

/** Find if there exists any pair of numbers which sum is equal to the value. */
func (this *TwoSum) Find(value int) bool {
    
    for num, cnt := range this.store {
        _, ok := this.store[value - num]
        if (num != value - num && ok) || (num == value - num && cnt > 1) {
            return true
        }
    }
    
    return false
}

/**
 * Your TwoSum object will be instantiated and called as such:
 * obj := Constructor();
 * obj.Add(number);
 * param_2 := obj.Find(value);
 */
```
