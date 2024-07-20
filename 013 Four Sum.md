# Four Sum :-

[Problem Link] :--- (https://leetcode.com/problems/4sum/)

<h3>
Given an array nums of n integers, return an array of all the unique quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:<br>
0 <= a, b, c, d < n<br>
a, b, c, and d are distinct.<br>
nums[a] + nums[b] + nums[c] + nums[d] == target<br>
You may return the answer in any order.<br><br>

Example 1:<br>
Input: nums = [1,0,-1,0,-2,2], target = 0<br>
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]<br><br>

Example 2:<br>
Input: nums = [2,2,2,2,2], target = 8<br>
Output: [[2,2,2,2]]<br><br>
 
Constraints:<br><br>
1 <= nums.length <= 200<br>
-109 <= nums[i] <= 109<br>
-109 <= target <= 109<br><br>
  
</h3>

***Solution***

```
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        int n=nums.size();
        vector<vector<int>>ans;
        sort(nums.begin(),nums.end());

        for(int a=0;a<n;a++)
        {
            for(int b=a+1;b<n;b++)
            {
                int c=b+1;
                int d=n-1;
                while(c<d)
                {
                    long long sum=nums[a];
                    sum+=nums[b];
                    sum+=nums[c];
                    sum+=nums[d];
                    if(sum<target)
                    {
                        c++;
                    }
                    else if(sum>target)
                    {
                        d--;
                    }
                    else
                    {
                        vector<int>v={nums[a],nums[b],nums[c],nums[d]};
                        if(find(ans.begin(),ans.end(),v)==ans.end()) 
                        {
                            ans.push_back(v);
                        }
                        c++;
                        d--;
                    }
                }
            }
        }
        return ans;
    }
};

```
