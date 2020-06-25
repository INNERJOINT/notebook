# Thinking
1. 利用哈希表


----
# Problems

1. Two Sum
    <br>
    Given nums=[2,7,11,15],target=9;
    <br>return [0,1]
```go
func twoSum(nums []int, target int) []int {
    v := make(map[int]int)
    for i:=0;i< len(nums);i++{
        dif:=target -nums[i]
        c,ok:=v[dif]
        if ok!= false{
            return []int{c,i}
        }
        v[nums[i]]=i
    }
    return []int{-1,-1}
}
```
方法1:暴力法<br>
方法2:哈希表法，以nums[i]为key，i为value即可快速找出

2. Add Two Numbers
```go
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    dummy := new(ListNode)
    curr := dummy
    carry := 0

    for (l1 != nil || l2 != nil || carry > 0){
        curr.Next = new(ListNode)
        curr = curr.Next
        if l1 != nil {
            carry += l1.Val
            l1 = l1.Next
        }
        if l2 != nil {
            carry += l2.Val
            l2 = l2.Next
        }
        curr.Val = carry % 10
        carry /= 10
    }
    return dummy.Next
}
```
很简单，