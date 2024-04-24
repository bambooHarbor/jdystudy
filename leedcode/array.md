# [704. 二分查找](https://leetcode.cn/problems/binary-search/)

给定一个 `n` 个元素有序的（升序）整型数组 `nums` 和一个目标值 `target` ，写一个函数搜索 `nums` 中的 `target`，如果目标值存在返回下标，否则返回 `-1`。
**示例 1:**

```
输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4
```

**示例 2:**

```
输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1
```

**提示：**

1. 你可以假设 `nums` 中的所有元素是不重复的。
2. `n` 将在 `[1, 10000]`之间。
3. `nums` 的每个元素都将在 `[-9999, 9999]`之间。

**二分法的前提：有序，无重复 ；  注意：边界问题，左闭右闭，左闭右开**

~~~java
//左闭右闭
class Solution{
    public int search (int[] nums, int target){
        int left = 0;
        int right = nums.length - 1; //左闭右闭
        while(left <= right)
        {
            int middle = (left + right) >> 1 ;
            if(nums[middle] == target)
            {
                return middle;
            }
            if(nums[middle] > target) //目标比中间值小  往左缩进
            {
                right = middle - 1;//原来的那个位置已经用过了（左闭右开时没有这种情况）
            }else//目标比中间值大  往右缩进
            {
                left = middle + 1;//原来的那个位置已经用过了
            }
        }
        return -1;
    }
}
~~~



~~~java
//左闭右开
class Solution{
    public int search (int[] nums, int target){
        int left = 0;
        int right = nums.length ; //左闭右开 修改位置1
        while(left < right) //左闭右开 修改位置2
        {
            int middle = (left + right) >> 1 ;
            if(nums[middle] == target)
            {
                return middle;
            }
            if(nums[middle] > target) 
            {
                right = middle ; //左闭右开 修改位置3
            }else
            {
                left = middle + 1;
            }
        }
        return -1;
    }
}
~~~



# [27. 移除元素](https://leetcode.cn/problems/remove-element/)

给你一个数组 `nums` 和一个值 `val`，你需要 **[原地](https://baike.baidu.com/item/原地算法)** 移除所有数值等于 `val` 的元素，并返回移除后数组的新长度。

不要使用额外的数组空间，你必须仅使用 `O(1)` 额外空间并 **[原地 ](https://baike.baidu.com/item/原地算法)修改输入数组**。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

**示例 1：**

```
输入：nums = [3,2,2,3], val = 3
输出：2, nums = [2,2]
解释：函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。你不需要考虑数组中超出新长度后面的元素。例如，函数返回的新长度为 2 ，而 nums = [2,2,3,3] 或 nums = [2,2,0,0]，也会被视作正确答案。
```

**示例 2：**

```
输入：nums = [0,1,2,2,3,0,4,2], val = 2
输出：5, nums = [0,1,3,0,4]
解释：函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。注意这五个元素可为任意顺序。你不需要考虑数组中超出新长度后面的元素。
```

 **提示：**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

三种方法：

**第一种：前后指针（双指针）**

~~~java
class Solution{
    public int removeElement(int[] nums, int val){
        //前后指针
        //前指针负责往后走（需要判断原来位置是否符合要求，交换的时候后指针才往前走）
        int left = 0;
        int right = nums.length - 1;
        int len = nums.length;
        while(left <= right)
        {
            if(nums[left] == val)
            {
                nums[left] = nums[right];
                right--;
                len--;
            }else
            {
                left++;
            }
        }
        return len;
    }
}
~~~

**第二种：快慢指针（双指针）**

~~~java
class Solution{
    public int removeElement(int[] nums, int val){
        //快慢指针
        //快指针每走一步和慢指针交换；当快指针检测到val值的时候则多加一步
        int slow = 0 ;
        int fast = 0 ;
        int len = nums.length;
        for(; fast < len; fast++)
        {
            if(nums[fast] != val)
            {
                nums[slow] = nums[fast];
                slow++;
            }
        }
        return slow;
    }
}
~~~

**第三种：暴力解法**

~~~java
class Solution{
    public int removeElement(int[] nums, int val)
    {
        int len = nums.length;
        for(int i = 0; i < len; i++)
        {
            if(nums[i] == val)
            {
                for(int j = i + 1 ; j < len ; j++)
                {
                    nums[j - 1] = nums[j];
                }
                len--;
                i--;
            }
        }
        return len;
    }
}
~~~























































































































































































