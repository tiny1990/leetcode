# 29. 两数相除
给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。  

返回被除数 dividend 除以除数 divisor 得到的商。  

示例 1:  
```
输入: dividend = 10, divisor = 3
输出: 3
```
示例 2:  
```
输入: dividend = 7, divisor = -3
输出: -2
```
说明:
- 被除数和除数均为 32 位有符号整数。
- 除数不为 0。
- 假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−2^31,  2^31 − 1]。本题中，如果除法结果溢出，则返回 2^31 − 1。

```go
func divide(dividend int, divisor int) int {
}
```

## 解题思路
二分法不太容易想到  
根据说明判断好边界，先判断出最终结果的正负号，然后将所有的数字转换正数  
通过左移n位 (乘以n个2)，来缩小范围  
被除数减去这个数

## 题解

```go
func divide(dividend int, divisor int) int {
    
    if dividend == -(1<<31) && divisor == -1 {
        return (1<<31)-1;
    }
    
    isNegative := false
    if (dividend < 0 && divisor > 0) || (dividend > 0 && divisor < 0) {
        isNegative = true
    }
    
    if dividend < 0 {
        dividend = -dividend
    }
    if divisor < 0 {
        divisor = -divisor
    }
    
    result := 0
    for dividend >= divisor {
        
        var shift uint
        for dividend >= (divisor << shift) {
            shift++
        }
        dividend -= divisor << (shift - 1)
        result += 1 << (shift - 1)
    }
    
    if isNegative {
        return -result
    }
    
    return result
}

```
