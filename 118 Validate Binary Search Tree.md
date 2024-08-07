# Validate Binary Search Tree :-

[Problem Link] :--- (https://leetcode.com/problems/validate-binary-search-tree/description/)

<h3>
Given the root of a binary tree, determine if it is a valid binary search tree (BST).
<br>
A valid BST is defined as follows:<br>

The left subtree of a node contains only nodes with keys less than the node's key.<br>
The right subtree of a node contains only nodes with keys greater than the node's key.<br>
Both the left and right subtrees must also be binary search trees.<br><br>

Example 1:<br>
Input: root = [2,1,3]<br>
Output: true<br><br>
Example 2:<br>


Input: root = [5,1,4,null,null,3,6]<br>
Output: false<br>
Explanation: The root node's value is 5 but its right child's value is 4.<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 104].<br>
-231 <= Node.val <= 231 - 1<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isValidBST(TreeNode* root, TreeNode* minNode = nullptr, TreeNode* maxNode = nullptr) {
        if (!root) return true;

        if (minNode && root->val <= minNode->val) {
            return false;
        }
        if (maxNode && root->val >= maxNode->val) {
            return false;
        }

        return isValidBST(root->left, minNode, root) && isValidBST(root->right, root, maxNode);
    }
};

```
