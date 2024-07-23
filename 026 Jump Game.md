# Jump Game :-

[Problem Link] :--- (https://leetcode.com/problems/jump-game/description/)

<h3>
You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.<br><br>
Return true if you can reach the last index, or false otherwise..<br><br>

Example 1:<br>
Input: nums = [2,3,1,1,4]<br>
Output: true<br>
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.<br><br>

Example 2:<br>
Input: nums = [3,2,1,0,4]<br>
Output: false<br>
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.<br><br>
 
Constraints:<br><br>
1 <= nums.length <= 104<br>
0 <= nums[i] <= 105<br>
  
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
