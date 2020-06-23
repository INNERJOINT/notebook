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
