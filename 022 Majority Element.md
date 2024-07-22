# Majority Element :-

[Problem Link] :--- (https://leetcode.com/problems/majority-element/description/)

<h3>
Given an array nums of size n, return the majority element.<br><br>
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.<br><br>

Example 1:<br>
Input: nums = [3,2,3]<br>
Output: 3<br>

Example 2:<br>
Input: nums = [2,2,1,1,1,2,2]<br>
Output: 2<br>
 
Constraints:<br><br>
n == nums.length<br>
1 <= n <= 5 * 104<br>
-109 <= nums[i] <= 109<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n = nums.size();
        return nums[n/2];
    }
};

```
