# Sort Colors :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.<br>
We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.<br>
You must solve this problem without using the library's sort function.<br>
<br><br>
Example 1:<br>
Input: nums = [2,0,2,1,1,0]<br>
Output: [0,0,1,1,2,2]<br>
  
Example 2:<br>
Input: nums = [2,0,1]<br>
Output: [0,1,2]<br>
 
Constraints: <br>
n == nums.length<br>
1 <= n <= 300<br>
nums[i] is either 0, 1, or 2.<br><br>
Follow up: Could you come up with a one-pass algorithm using only constant extra space?
  
</h3>

***Solution***

```

#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
    void sortColors(vector<int>& nums) {
        sort(nums.begin() , nums.end());
    }
};

```
