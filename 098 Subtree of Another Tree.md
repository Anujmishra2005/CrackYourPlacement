# Subtree of Another Tree :-

[Problem Link] :--- (https://leetcode.com/problems/subtree-of-another-tree/description/)

<h3>
Given the roots of two binary trees root and subRoot, return true if there is a subtree of root with the same structure and node values of subRoot and false otherwise.
<br><br>
A subtree of a binary tree tree is a tree that consists of a node in tree and all of this node's descendants. The tree tree could also be considered as a subtree of itself..<br><br>

Example 1:<br>
Input: root = [3,4,5,1,2], subRoot = [4,1,2]<br>
Output: true<br><br>
Example 2:<br>


Input: root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]<br>
Output: false<br><br>
 

Constraints:<br><br>

The number of nodes in the root tree is in the range [1, 2000].<br>
The number of nodes in the subRoot tree is in the range [1, 1000].<br>
-104 <= root.val <= 104<br>
-104 <= subRoot.val <= 104<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        if(subRoot==NULL)
            return true;
        if(root==NULL)
            return false;
        if(isidentical(root,subRoot))
            return true;
        return isSubtree(root->left,subRoot) || isSubtree(root->right,subRoot);
    }

    bool isidentical(TreeNode* a, TreeNode* b){
        if(a==NULL && b==NULL)
            return true;
        if(a==NULL || b==NULL)
            return false;
        if(a->val!=b->val)
            return false;
        return isidentical(a->left,b->left) && isidentical(a->right,b->right);
    }
};

```
