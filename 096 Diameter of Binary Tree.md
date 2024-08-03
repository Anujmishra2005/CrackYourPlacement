# Diameter of Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/diameter-of-binary-tree/description/)

<h3>
Given the root of a binary tree, return the length of the diameter of the tree.
<br><br>
The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.
<br><br>
The length of a path between two nodes is represented by the number of edges between them.<br><br>

Example 1:<br>
Input: root = [1,2,3,4,5]<br>
Output: 3<br>
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].<br><br>
Example 2:<br>
Input: root = [1,2]<br>
Output: 1<br><br>
 

Constraints:<br><br>
The number of nodes in the tree is in the range [1, 104].<br>
-100 <= Node.val <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int height(TreeNode* root, int &diameter){
        if(!root) return 0;
        int lh=height(root->left, diameter);
        int rh=height(root->right, diameter);
        diameter=max(diameter,lh+rh);
        return 1+max(lh, rh);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        int diameter=0;
        height(root, diameter);
        return diameter;
    }
};

```
