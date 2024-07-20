# Find All Duplicates in an Array :-

[Problem Link] :--- (https://leetcode.com/problems/find-all-duplicates-in-an-array/description/)

<h3>
Given an integer array nums of length n where all the integers of nums are in the range [1, n] and each integer appears once or twice, return an array of all the integers that appears twice.<br><br>

You must write an algorithm that runs in O(n) time and uses only constant extra space.<br><br>
Example 1:<br>
Input: nums = [4,3,2,7,8,2,3,1]<br>
Output: [2,3]<br><br>

Example 2:<br>
Input: nums = [1,1,2]<br>
Output: [1]<br><br>

Example 3:<br>
Input: nums = [1]<br>
Output: []<br><br>
 
Constraints:<br>
n == nums.length<br>
1 <= n <= 105<br>
1 <= nums[i] <= n<br><br>
Each element in nums appears once or twice.<br>
  
</h3>

***Solution***

```
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int>ans;
        for(int i=0;i<nums.size();i++)
        {
            int x = abs(nums[i]);
            if(nums[x-1]<0)
            {
                ans.push_back(x);
            }
            nums[x-1]*=-1;
        }
        return ans;
    }
};

```
