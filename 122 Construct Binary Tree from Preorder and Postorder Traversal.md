# Construct Binary Tree from Preorder and Postorder Traversal :-

[Problem Link] :--- (https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/)

<h3>
Given two integer arrays, preorder and postorder where preorder is the preorder traversal of a binary tree of distinct values and postorder is the postorder traversal of the same tree, reconstruct and return the binary tree.
<br><br>
If there exist multiple answers, you can return any of them.<br><br>

Example 1:<br>
Input: preorder = [1,2,4,5,3,6,7], postorder = [4,5,2,6,7,3,1]<br>
Output: [1,2,3,4,5,6,7]<br><br>
Example 2:<br>

Input: preorder = [1], postorder = [1]<br>
Output: [1]<br>
 

Constraints:<br><br>

1 <= preorder.length <= 30<br>
1 <= preorder[i] <= preorder.length<br>
All the values of preorder are unique.<br>
postorder.length == preorder.length<br>
1 <= postorder[i] <= postorder.length<br>
All the values of postorder are unique.<br>
It is guaranteed that preorder and postorder are the preorder traversal and postorder traversal of the same binary tree.<br><br>
  
</h3>

***Solution***

```


class Solution {
public:
    TreeNode* constructFromPrePost(vector<int> pre, vector<int> post) {
        vector<TreeNode*> s;
        s.push_back(new TreeNode(pre[0]));
        for (int i = 1, j = 0; i < pre.size(); ++i) {
            TreeNode* node = new TreeNode(pre[i]);
            while (s.back()->val == post[j])
                s.pop_back(), j++;
            if (s.back()->left == NULL) s.back()->left = node;
            else s.back()->right = node;
            s.push_back(node);
        }
        return s[0];
    }
};

```
