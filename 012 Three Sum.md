# Three Sum :-

[Problem Link] :--- (https://leetcode.com/problems/3sum/description/)

<h3>
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.<br><br>

Notice that the solution set must not contain duplicate triplets.<br><br>

Example 1:<br>
Input: nums = [-1,0,1,2,-1,-4]<br>
Output: [[-1,-1,2],[-1,0,1]]<br>
Explanation: <br>
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.<br>
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.<br>
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.<br>
The distinct triplets are [-1,0,1] and [-1,-1,2].<br>
Notice that the order of the output and the order of the triplets does not matter.<br><br>

Example 2:<br>
Input: nums = [0,1,1]<br>
Output: []<br>
Explanation: The only possible triplet does not sum up to 0.<br><br>

Example 3: <br>
Input: nums = [0,0,0] <br>
Output: [[0,0,0]]<br>
Explanation: The only possible triplet sums up to 0.<br>
 
Constraints:<br><br>
3 <= nums.length <= 3000<br>
-105 <= nums[i] <= 105<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        int target = 0;
        sort(nums.begin(), nums.end());
        set<vector<int>> s;
        vector<vector<int>> output;
        for (int i = 0; i < nums.size(); i++){
            int j = i + 1;
            int k = nums.size() - 1;
            while (j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                if (sum == target) {
                    s.insert({nums[i], nums[j], nums[k]});
                    j++;
                    k--;
                } else if (sum < target) {
                    j++;
                } else {
                    k--;
                }
            }
        }
        for(auto triplets : s)
            output.push_back(triplets);
        return output;
    }
};

```
