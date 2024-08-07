# Binary Tree Right Side View :-

[Problem Link] :--- (https://leetcode.com/problems/binary-tree-right-side-view/description/)

<h3>
Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.<br><br>

Example 1:<br>
Input: root = [1,2,3,null,5,null,4]<br>
Output: [1,3,4]<br><br>
Example 2:<br>

Input: root = [1,null,3]<br>
Output: [1,3]<br><br>
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
    vector<int> rightSideView(TreeNode* root) {
        vector<int>ans;
        queue<TreeNode*> q;
        if(root==NULL)
        return ans;
        q.push(root);
        while(1)
        {
            int size=q.size();
            if(size==0)
            return ans;
            vector<int> data;
            while(size--)
            {
                TreeNode* temp=q.front();
                q.pop();
                data.push_back(temp->val);
                if(temp->left!=NULL)
                q.push(temp->left);
                if(temp->right!=NULL)
                q.push(temp->right);
            }
            ans.push_back(data.back());
        }
    }
};

```
