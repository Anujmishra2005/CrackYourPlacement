# Path Sum :-

[Problem Link] :--- (https://leetcode.com/problems/path-sum/description/)

<h3>
Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.
<br>
A leaf is a node with no children.<br><br>

Example 1:<br>
Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22<br>
Output: true<br>
Explanation: The root-to-leaf path with the target sum is shown.<br><br>
Example 2:<br>
Input: root = [1,2,3], targetSum = 5<br>
Output: false<br>
Explanation: There two root-to-leaf paths in the tree:<br>
(1 --> 2): The sum is 3.<br>
(1 --> 3): The sum is 4.<br>
There is no root-to-leaf path with sum = 5.<br><br>
Example 3:<br>

Input: root = [], targetSum = 0<br>
Output: false<br>
Explanation: Since the tree is empty, there are no root-to-leaf paths.<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 5000].<br>
-1000 <= Node.val <= 1000<br>
-1000 <= targetSum <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) {
        if(!root){
            return false;
        }
        if(!root->left && !root->right && targetSum -root->val==0){
            return true;
        }

        return hasPathSum(root->left, targetSum-root->val) || hasPathSum(root->right, targetSum-root->val);
        
    }
};
```
