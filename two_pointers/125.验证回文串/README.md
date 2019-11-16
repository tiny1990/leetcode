# 125. 验证回文串
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。  

说明：本题中，我们将空字符串定义为有效的回文串。  

示例 1:
```
输入: "A man, a plan, a canal: Panama"
输出: true
```
示例 2:
```
输入: "race a car"
输出: false
```


```go
func isPalindrome(s string) bool {
}
```

## 解题思路
```
// step.1 toLower
// step.2 filter
// step.3 reverse
// step.4 equal

```
## 题解

```go
func isPalindrome(s string) bool {
    s = strings.ToLower(s)
    byteArray := make([]rune,0)
    
    for _,b := range s {
        if (b >= '0' && b <= '9') || (b >= 'a' && b <= 'z') {
            byteArray = append(byteArray, b)
        }
    }

    s = string(byteArray)
    reverse(byteArray)

    return s == string(byteArray)

}

func reverse(byteArray []rune) {
    for i,j := 0, len(byteArray) - 1; i < j; {
        byteArray[i], byteArray[j] = byteArray[j], byteArray[i]
        i++
        j--
    }
}
```
