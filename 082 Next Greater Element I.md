#  Next Greater Element I :-

[Problem Link] :--- (https://leetcode.com/problems/next-greater-element-i/description/)

<h3>
The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.<br>
You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.<br>
For each 0 <= i < nums1.length  find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.
<br>
Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.<br><br>

Example 1:<br>
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]<br>
Output: [-1,3,-1]<br>
Explanation: The next greater element for each value of nums1 is as follows:<br>
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.<br>
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.<br>
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.<br><br>
Example 2:<br>

Input: nums1 = [2,4], nums2 = [1,2,3,4]<br>
Output: [3,-1]<br>
Explanation: The next greater element for each value of nums1 is as follows:<br>
- 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3.<br>
- 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.<br><br>
 

Constraints:<br><br>

1 <= nums1.length <= nums2.length <= 1000<br>
0 <= nums1[i], nums2[i] <= 104<br>
All integers in nums1 and nums2 are unique.<br>
All the integers of nums1 also appear in nums2.<br><br>
 

Follow up: Could you find an O(nums1.length + nums2.length) solution?<br><br>
  
</h3>

***Solution***

```


class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int> ans(nums1.size(), -1); 
        for (int i = 0; i < nums1.size(); i++){
            int j = 0;
            while(nums2[j] != nums1[i]){
                j++;
            }
            // search for the next greater element 
            for(int k = j + 1; k < nums2.size(); k++){
                if(nums2[k] > nums1[i]) {
                    ans[i] = nums2[k];
                    break;
                }
            }
        }
        return ans;
    }
};

```
