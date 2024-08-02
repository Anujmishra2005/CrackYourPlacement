# Sum of Subarray Minimums :-

[Problem Link] :--- (https://leetcode.com/problems/sum-of-subarray-minimums/description/)

<h3>
Given an array of integers arr, find the sum of min(b), where b ranges over every (contiguous) subarray of arr. Since the answer may be large, return the answer modulo 109 + 7.<br><br>

Example 1:<br>
Input: arr = [3,1,2,4]<br>
Output: 17<br>
Explanation: <br>
Subarrays are [3], [1], [2], [4], [3,1], [1,2], [2,4], [3,1,2], [1,2,4], [3,1,2,4]. <br>
Minimums are 3, 1, 2, 4, 1, 1, 2, 1, 1, 1.<br>
Sum is 17.<br><br>
Example 2:<br>

Input: arr = [11,81,94,43,3]<br>
Output: 444<br><br>
 

Constraints:<br><br>

1 <= arr.length <= 3 * 104<br>
1 <= arr[i] <= 3 * 104<br>
  
</h3>

***Solution***

```

using ll = long long;
const int MOD = 1e9 + 7;

class Solution {
public:
    int sumSubarrayMins(vector<int>& nums) {
        int length = nums.size();
        vector<int> left(length, -1);
        vector<int> right(length, length);
        stack<int> stk;

        for (int i = 0; i < length; ++i) {
            while (!stk.empty() && nums[stk.top()] >= nums[i]) {
                stk.pop();
            }
            if (!stk.empty()) {
                left[i] = stk.top();
            }
            stk.push(i);
        }

        stk = stack<int>();

        for (int i = length - 1; i >= 0; --i) {
            while (!stk.empty() && nums[stk.top()] > nums[i]) {
                stk.pop();
            }
            if (!stk.empty()) {
                right[i] = stk.top();
            }
            stk.push(i);
        }

        ll sum = 0;

        for (int i = 0; i < length; ++i) {
            sum += static_cast<ll>(i - left[i]) * (right[i] - i) * nums[i] % MOD;
            sum %= MOD;
        }

        return sum;
    }
};

```
