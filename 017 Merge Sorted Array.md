# Merge Sorted Array :-

[Problem Link] :--- (https://leetcode.com/problems/merge-sorted-array/)

<h3>
You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.<br><br>
Merge nums1 and nums2 into a single array sorted in non-decreasing order.<br><br>
The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.<br><br>

Example 1:<br>
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3<br>
Output: [1,2,2,3,5,6]<br>
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].<br>
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.<br><br>

Example 2:<br>
Input: nums1 = [1], m = 1, nums2 = [], n = 0<br>
Output: [1]<br>
Explanation: The arrays we are merging are [1] and [].<br>
The result of the merge is [1].<br><br>

Example 3:<br>
Input: nums1 = [0], m = 0, nums2 = [1], n = 1<br>
Output: [1]<br>
Explanation: The arrays we are merging are [] and [1].<br>
The result of the merge is [1].<br>
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.<br><br>

Constraints:<br><br>
nums1.length == m + n<br>
nums2.length == n<br>
0 <= m, n <= 200<br>
1 <= m + n <= 200<br>
-109 <= nums1[i], nums2[j] <= 109<br><br>
  
</h3>

***Solution***

```
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        for (int j = 0, i = m; j<n; j++){
            nums1[i] = nums2[j];
            i++;
        }
        sort(nums1.begin(),nums1.end());
    }
};

```
