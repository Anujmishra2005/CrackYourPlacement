# Binary Tree Paths :-

[Problem Link] :--- (https://leetcode.com/problems/binary-tree-paths/)

<h3>
Given the root of a binary tree, return all root-to-leaf paths in any order.
<br><br>
A leaf is a node with no children.<br><br>

Example 1:<br>
Input: root = [1,2,3,null,5]<br>
Output: ["1->2->5","1->3"]<br><br>
Example 2:<br>

Input: root = [1]<br>
Output: ["1"]<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 100].<br>
-100 <= Node.val <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
    public:
    vector<string> binaryTreePaths(TreeNode* root) {
        vector<string> result;
        dfs(root, "", result);
        return result;
    }

    void dfs(TreeNode* node, string path, vector<string>& result) {
        if (!node) return;
        path += to_string(node->val);
        if (!node->left && !node->right) {
            result.push_back(path);
        } else {
            dfs(node->left, path + "->", result);
            dfs(node->right, path + "->", result);
        }
    }
};

```
