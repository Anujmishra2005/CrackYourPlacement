# Minimum Absolute Difference in BST :-

[Problem Link] :--- (https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)

<h3>
Given the root of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two different nodes in the tree.<br><br>
Example 1:<br>
Input: root = [4,2,6,1,3]<br>
Output: 1<br><br>
Example 2:<br>


Input: root = [1,0,48,null,null,12,49]<br>
Output: 1<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [2, 104].<br>
0 <= Node.val <= 105<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
   TreeNode* prev = nullptr;
    int minDiff = INT_MAX;
    void inorder(TreeNode* node) {
        if (node==NULL) return;
        // Traverse the left subtree
        inorder(node->left);
        // Process the current node
        if(prev != NULL){
            minDiff = min(minDiff, node->val - prev->val);
        }
        prev = node;
        // Traverse the right subtree
        inorder(node->right);
    }
    int getMinimumDifference(TreeNode* root) {
           inorder(root);
        return minDiff;
    }
};
```
