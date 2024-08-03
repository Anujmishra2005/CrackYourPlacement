# Convert Sorted Array to Binary Search Tree :-

[Problem Link] :--- (https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)

<h3>
Given an integer array nums where the elements are sorted in ascending order, convert it to a height-balanced binary search tree.<br><br>

Example 1:<br>
Input: nums = [-10,-3,0,5,9]<br>
Output: [0,-3,9,-10,null,5]<br>
Explanation: [0,-10,5,null,-3,null,9] is also accepted:<br><br>

Example 2:<br>
Input: nums = [1,3]<br>
Output: [3,1]<br>
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.<br><br>
 

Constraints:<br><br>

1 <= nums.length <= 104<br>
-104 <= nums[i] <= 104<br>
nums is sorted in a strictly increasing order.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return helper(nums, 0, nums.size() - 1);
    }

private:
    TreeNode* helper(vector<int>& nums, int start, int end) {
        if (start > end) {
            return nullptr;
        }
        
        int mid = start + (end - start) / 2;
        TreeNode* root = new TreeNode(nums[mid]);
        root->left = helper(nums, start, mid - 1);
        root->right = helper(nums, mid + 1, end);
        
        return root;
    }
};
```
