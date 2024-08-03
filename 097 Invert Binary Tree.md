# Invert Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/invert-binary-tree/description/)

<h3>
Given the root of a binary tree, invert the tree, and return its root.<br><br>
Example 1:<br>
Input: root = [4,2,7,1,3,6,9]<br>
Output: [4,7,2,9,6,3,1]<br><br>
Example 2:<br>
Input: root = [2,1,3]<br>
Output: [2,3,1]<br><br>
Example 3:<br>
Input: root = []<br>
Output: []<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 100].<br>
-100 <= Node.val <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (root == nullptr) {
            return nullptr;
        }
        
        TreeNode* temp = root->left;
        root->left = root->right;
        root->right = temp;
        
        invertTree(root->left);
        invertTree(root->right);
        
        return root;        
    }
};

```
