# All Nodes Distance K in Binary Tree :-

[Problem Link] :--- (https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/description/)

<h3>
Given the root of a binary tree, the value of a target node target, and an integer k, return an array of the values of all nodes that have a distance k from the target node.
<br><br>
You can return the answer in any order.<br><br>

Example 1:<br>
Input: root = [3,5,1,6,2,0,8,null,null,7,4], target = 5, k = 2<br>
Output: [7,4,1]<br>
Explanation: The nodes that are a distance 2 from the target node (with value 5) have values 7, 4, and 1.<br><br>
Example 2:<br>

Input: root = [1], target = 1, k = 3<br>
Output: []<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [1, 500].<br>
0 <= Node.val <= 500<br>
All the values Node.val are unique.<br>
target is the value of one of the nodes in the tree.<br>
0 <= k <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    void build(TreeNode *root, unordered_map<int,vector<int>> &g)
    {
        if(root->left)
        {
            g[root->val].push_back(root->left->val);
            g[root->left->val].push_back(root->val);
            build(root->left,g);
        }

        if(root->right)
        {
            g[root->val].push_back(root->right->val);
            g[root->right->val].push_back(root->val);
            build(root->right,g);
        }
    }
    vector<int> distanceK(TreeNode* root, TreeNode* target, int k) {
        if(k==0)
        {
            vector<int> a;
            a.push_back(target->val);
            return a;
        }

        unordered_map<int,vector<int>> g;
        build(root,g);
        unordered_map<int,bool> vis;

        vector<int> ans;
        queue<int> q;
        int dist=0;

        q.push(target->val);

        while(!q.empty())
        {
            int n=q.size();
            while(n--)
            {
                int curr=q.front();
                q.pop();
                vis[curr]=true;
                for(auto it: g[curr])
                {
                    if(!vis[it])
                    {
                        q.push(it);
                    }
                }
            }
            dist++;
            if(dist==k)
            {
                while(!q.empty())
                {
                    ans.push_back(q.front());
                    q.pop();
                }
            }
        }
        return ans;
    }
};

```
