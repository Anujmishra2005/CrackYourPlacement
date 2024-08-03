# Symmetric Tree :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).<br><br>

Example 1:<br>
Input: root = [1,2,2,3,4,4,3]<br>
Output: true<br><br>
Example 2:<br>


Input: root = [1,2,2,null,3,null,3]<br>
Output: false<br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 1000].<br>
-100 <= Node.val <= 100<br><br>
 

Follow up: Could you solve it both recursively and iteratively?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isMirror(TreeNode* left, TreeNode* right) {
        if (left == NULL && right == NULL) return true; 
        if (left == NULL  || right == NULL ) return false;
        if (left->val != right->val) return false; 
        return isMirror(left->left, right->right) && isMirror(left->right, right->left);
    }

    bool isSymmetric(TreeNode* root) {
        if (root == NULL ) return true;
        return isMirror(root->left, root->right);
    }
};

```
