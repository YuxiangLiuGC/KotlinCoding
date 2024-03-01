###### 283. Move Zeroes
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
