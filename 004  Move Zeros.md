# Move Zeros :-

[Problem Link] :--- (https://leetcode.com/problems/move-zeroes/description/)

<h3>
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.<br><br>
Note that you must do this in-place without making a copy of the array.<br><br>
Example 1:<br>
Input: nums = [0,1,0,3,12]<br>
Output: [1,3,12,0,0]<br><br>
Example 2:<br>
Input: nums = [0]<br>
Output: [0]<br><br>
 
Constraints:<br>
1 <= nums.length <= 104<br>
-231 <= nums[i] <= 231 - 1<br>
  
</h3>

***Solution***

```

#include<bits/stdc++.h>
using namespace std;
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int j=0 , k=0;
        for(int i=0;i<nums.size();i++)
        {
            if (nums[i] != 0)
            {
                swap(nums[i],nums[j]);
                j++;
            }
        }
        for(int i=0;i<nums.size();i++)
        {
            cout << nums[i] << endl;
        }
    }
};

```
