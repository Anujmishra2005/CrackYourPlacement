# Subarrays Sum Divisible by K :-

[Problem Link] :--- (https://leetcode.com/problems/subarray-sums-divisible-by-k/description/)

<h3>
Given an integer array nums and an integer k, return the number of non-empty subarrays that have a sum divisible by k.<br><br>

A subarray is a contiguous part of an array.<br><br>

Example 1:<br>
Input: nums = [4,5,0,-2,-3,1], k = 5<br>
Output: 7<br>
Explanation: There are 7 subarrays with a sum divisible by k = 5:<br>
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]<br><br>

Example 2:<br>
Input: nums = [5], k = 9<br>
Output: 0<br><br>
 
Constraints:<br><br>
1 <= nums.length <= 3 * 104<br>
-104 <= nums[i] <= 104<br>
2 <= k <= 104<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int subarraysDivByK(vector<int>& nums, int k) {
        int n = nums.size();
        int sum = 0;
        int count = 0;

        unordered_map<int, int> m;
        m[0] = 1;

        for (int i : nums) {
            sum += i;
            int mod = sum % k;
            if (mod < 0)
                mod += k;
            if (m.find(mod) != m.end()) {
                count += m[mod];
            }
            m[mod]++;
        }

        return count;
    }
};

```
