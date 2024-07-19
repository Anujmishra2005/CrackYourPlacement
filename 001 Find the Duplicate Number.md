# Find the Duplicate Number :-

<h3>
  Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.
There is only one repeated number in nums, return this repeated number.
You must solve the problem without modifying the array nums and uses only constant extra space.
<br>
Example 1: <br>
Input: nums = [1,3,4,2,2] <br>
Output: 2<br>

Example 2:<br>
Input: nums = [3,1,3,4,2]<br>
Output: 3<br>

Example 3:<br>
Input: nums = [3,3,3,3,3]<br>
Output: 3<br>
 
Constraints:
1 <= n <= 105
nums.length == n + 1
1 <= nums[i] <= n
All the integers in nums appear only once except for precisely one integer which appears two or more times.
  
</h3>

[Problem Link] :--- (https://leetcode.com/problems/find-the-duplicate-number/description/)

***Solution***

```

#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin() , nums.end());
        for(int i=0;i< nums.size()-1;++i)
        {
            if (nums[i] == nums[i+1])
            {
                return nums[i];
            }
        }
        return -1;
    }
};

```
