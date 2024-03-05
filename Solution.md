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
## 1299. Replace Elements with Greatest Element on Right Side
(1) nested loop
```kotlin
class Solution {
    fun replaceElements(arr: IntArray): IntArray {
        for(i in arr.indices){
            var j = i+1
            var max = -1
            while(j<arr.size){
                if(arr[j]>max){
                    max = arr[j]
                }
                j++
            }
            arr[i] = max
        }
        return arr
    }
}
```
(2) backward one loop
```kotlin
class Solution {
    fun replaceElements(arr: IntArray): IntArray {
        var max = -1
        for(i in arr.lastIndex downTo 0){
            val temp = arr[i]
            arr[i] = max
            max = maxOf(max, temp)
        }
        return arr
    }
}
```
## 1. Two Sum
```kotlin
class Solution {
    fun twoSum(nums: IntArray, target: Int): IntArray {
       
        for(i in 0 until nums.size){
            for(j in i+1 until nums.size){
                if(nums[i]+nums[j]==target){
                    return intArrayOf(i, j)
                }
            }
        }
        return IntArray(2)
    }
}
```
