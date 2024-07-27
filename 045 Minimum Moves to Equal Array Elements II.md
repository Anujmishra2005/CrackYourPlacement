# Minimum Moves to Equal Array Elements II :-

[Problem Link] :--- (https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/description/)

<h3>
Given an integer array nums of size n, return the minimum number of moves required to make all array elements equal.
<br><br>
In one move, you can increment or decrement an element of the array by 1.
<br><br>
Test cases are designed so that the answer will fit in a 32-bit integer..<br><br>

Example 1:<br>
Input: nums = [1,2,3]<br>
Output: 2<br>
Explanation:<br>
Only two moves are needed (remember each move increments or decrements one element):<br>
[1,2,3]  =>  [2,2,3]  =>  [2,2,2]<br><br>
Example 2:<br>

Input: nums = [1,10,2,9]<br>
Output: 16<br>
 
Constraints:<br>
n == nums.length<br>
1 <= nums.length <= 105<br>
-109 <= nums[i] <= 109<br>
  
</h3>

***Solution***

```

class Solution {
public:
    int minMoves2(vector<int>& nums) 
    {
        sort(nums.begin(), nums.end());
        int mid = nums[nums.size()/2];
        int ans = 0;
        for(auto val:nums)
            ans += abs(mid - val);
        return ans;
    }
};

```
