## 283. Move Zeroes
(1) Not in place
```Kotlin
class Solution {
    fun moveZeroes(nums: IntArray): Unit {
        val array = Array(nums.size){0}
        var j = 0
        for(i in nums.indices){
            if(nums[i]!=0){
                array[j]=nums[i]
                j++
            }
        }
        array.forEach { println(it) }
    }
}
```
(2) stupid two pointer
```Kotlin
class Solution {
    fun moveZeroes(nums: IntArray): Unit {
        var slow = 0
        var fast = 0
        while(slow<nums.size && fast<nums.size){
            if(slow==fast){
                if(nums[slow]!=0){
                    slow++
                    fast++
                }else{
                    fast++
                }
            }else if(nums[slow]==0 && nums[fast]!=0){
                val temp = nums[slow]
                nums[slow] = nums[fast]
                nums[fast] = temp
                slow++
                fast++
            }else if(nums[slow]!=0 && nums[fast]==0){
                slow++
                fast++
            }else if(nums[slow]==0 && nums[fast]==0){
                fast++
            }else if(nums[slow]!=0 && nums[fast]!=0){
                slow++
                fast++
            }
            
        }
    }
}
```
(2) smart pointer
```kotlin
class Solution {
    fun moveZeroes(nums: IntArray): Unit {
       var slow = 0
       for(fast in nums.indices){
           if(nums[fast]!=0){
               nums[slow] = nums[fast]
               slow++
           }
       }
       while(slow<nums.size){
           nums[slow] = 0
           slow++
       }
    }
}
```
