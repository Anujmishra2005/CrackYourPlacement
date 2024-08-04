# Maximum Depth of Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/maximum-depth-of-binary-tree/)

<h3>
Given the root of a binary tree, return its maximum depth.
<br><br>
A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.<br><br>

Example 1:<br>
Input: root = [3,9,20,null,null,15,7]<br>
Output: 3<br><br>
Example 2:<br>

Input: root = [1,null,2]<br>
Output: 2<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 104].<br>
-100 <= Node.val <= 100<br>
  
</h3>

***Solution***

```

class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == NULL){
            return 0;
        }
        int leftDepth = 1 + maxDepth(root->left);
        int rightDepth = 1 + maxDepth(root->right);
        return  max(leftDepth, rightDepth);
    }
};

```
