# Balanced Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/balanced-binary-tree/description/)

<h3>
Given a binary tree, determine if it is height-balanced.<br><br>

Example 1:<br>
Input: root = [3,9,20,null,null,15,7]<br>
Output: true<br><br>
Example 2:<br>


Input: root = [1,2,2,3,3,null,null,4,4]<br>
Output: false<br><br>
Example 3:<br>

Input: root = []<br>
Output: true<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 5000].<br>
-104 <= Node.val <= 104<br>
  
</h3>

***Solution***

```


class Solution {
public:
    
    int levelsOfTree(TreeNode* root){
        if(root==NULL) return 0; 
        return 1 + max(levelsOfTree(root->left),levelsOfTree(root->right));
    }
   
    bool isBalanced(TreeNode* root) {
        if (root == NULL) return true;
    
        int LST = levelsOfTree(root->left);
        int RST = levelsOfTree(root->right);
        
        if(abs(LST-RST) > 1) return false;
        bool leftBalanced = isBalanced(root->left);
        bool rightBalanced = isBalanced(root->right);
        return leftBalanced && rightBalanced;  
    }
};

```
