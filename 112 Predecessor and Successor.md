# Predecessor and Successor :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/predecessor-and-successor/1)

<h3>
There is BST given with the root node with the key part as an integer only. You need to find the in-order successor and predecessor of a given key. If either predecessor or successor is not found, then set it to NULL.
<br><br>
Note:- In an inorder traversal the number just smaller than the target is the predecessor and the number just greater than the target is the successor. <br><br>

Example 1:<br>
Input:<br>
      8<br>
    /   \<br>
   1     9<br>
    \     \<br>
     4    10<br>
    /<br>
   3<br><br>
key = 8 <br>
Output: 4 9<br>
Explanation: 
In the given BST the inorder predecessor of 8 is 4 and inorder successor of 8 is 9.<br><br>
Example 2:<br>

Input:<br>
        10<br>
      /   \<br>
     2    11<br>
   /  \ <br>
  1    5<br>
      /  \<br>
     3    6<br>
      \<br>
       4<br><br>
key = 11<br>
Output: 10 -1<br>
Explanation:In given BST, the inorder predecessor of 11 is 10 whereas it does not have any inorder successor.<br><br>
Your Task: You don't need to print anything. You need to update pre with the predecessor of the key or NULL if the predecessor doesn't exist and succ to the successor of the key or NULL if the successor doesn't exist. pre and succ are passed as an argument to the function findPreSuc(). Please note, The key may be located either inside or outside the tree.<br><br>

Expected Time Complexity: O(Height of the BST).<br>
Expected Auxiliary Space: O(Height of the BST).<br><br>

Constraints: <br><br>
1 <= Number of nodes <= 104<br>
1 <= key of node <= 107<br>
1 <= key <= 107<br><br>
  
</h3>

***Solution***

```

class Solution
{
    public:
    void in(Node* root,vector<int>&v){
        if(!root){
            return ;
        }
        in(root->left,v);
        v.push_back(root->key);
        in(root->right,v);
    }
    void findPreSuc(Node* root, Node*& pre, Node*& suc, int key)
    {
        // Your code goes here
        vector<int>v;
        in(root,v);
        int ind=lower_bound(v.begin(),v.end(),key)-v.begin();
        pre=NULL;
        if(ind-1>=0){
            pre=new Node(v[ind-1]);
        }
        suc=NULL;
        if(ind<v.size()&&v[ind]!=key){
            suc=new Node(v[ind]);
        }
        else{
            if(ind+1<v.size()){
                suc=new Node(v[ind+1]);
            }
        }
        
    }
};

```
