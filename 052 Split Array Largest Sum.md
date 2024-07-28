# Split Array Largest Sum :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
Given an integer array nums and an integer k, split nums into k non-empty subarrays such that the largest sum of any subarray is minimized.
<br><br>
Return the minimized largest sum of the split.
<br><br>
A subarray is a contiguous part of the array.<br><br>
Example 1:<br>
Input: nums = [7,2,5,10,8], k = 2<br>
Output: 18<br>
Explanation: There are four ways to split nums into two subarrays.<br>
The best way is to split it into [7,2,5] and [10,8], where the largest sum among the two subarrays is only 18.<br><br>
Example 2:
<br>
Input: nums = [1,2,3,4,5], k = 2<br>
Output: 9<br>
Explanation: There are four ways to split nums into two subarrays.<br>
The best way is to split it into [1,2,3] and [4,5], where the largest sum among the two subarrays is only 9.<br><br>
 
Constraints:<br><br>
1 <= nums.length <= 1000<br>
0 <= nums[i] <= 106<br>
1 <= k <= min(50, nums.length)<br>
  
</h3>

***Solution***

```

class Solution {
public:
    // Similar to book allocation

    bool solve(vector<int>& a,int mid, int n, int m)
    {
        int sc=1;
        long long sum=0;
        for(int i=0;i<n;++i)
        {
            if(sum+a[i]>mid)
            {
                sc++;
                sum=a[i];
                if(sc>m || a[i]>mid) return false; //edge case
            }
            else
            {
                sum+=a[i];
            }
            
        }
        return true;
    }
    int splitArray(vector<int>& nums, int k) {
        int n=nums.size();
        int sum=0;
        for(int i=0;i<n;++i)
        {
            sum+=nums[i];
        }
        int s=0;
        int e=sum;
        int ans=-1;
        while(s<=e)
        {
            int mid=s+(e-s)/2;
            if(solve(nums,mid,n,k))
            {
                ans=mid;
                e=mid-1;
            }
            else
            {
                s=mid+1;
            }
        }
        return ans;
    
    }
};

```
