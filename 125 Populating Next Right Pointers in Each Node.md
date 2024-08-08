# Populating Next Right Pointers in Each Node :-

[Problem Link] :--- (https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

<h3>
You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:
<br><br>
struct Node {<br>
  int val;<br>
  Node *left;<br>
  Node *right;<br>
  Node *next;<br>
}<br><br>
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.<br><br>

Initially, all next pointers are set to NULL.<br><br>

Example 1:<br>
Input: root = [1,2,3,4,5,6,7]<br>
Output: [1,#,2,3,#,4,5,6,7,#]<br>
Explanation: Given the above perfect binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.<br><br>
Example 2:<br>

Input: root = []<br>
Output: []<br><br>
 

Constraints:<br><br>

The number of nodes in the tree is in the range [0, 212 - 1].<br>
-1000 <= Node.val <= 1000<br><br>
 

Follow-up:<br><br>

You may only use constant extra space.<br>
The recursive approach is fine. You may assume implicit stack space does not count as extra space for this problem.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    Node* connect(Node* root) {
        if(!root) return nullptr;
        queue<Node*> q;
        q.push(root);        
        while(size(q)) {
            Node* rightNode = nullptr;                   
            for(int i = size(q); i; i--) {              
                auto cur = q.front(); q.pop();        
                cur -> next = rightNode;           
                rightNode = cur;             
                if(cur -> right)       
                    q.push(cur -> right),    
                    q.push(cur -> left);       
            }
        }
        return root;
    }
};

```
