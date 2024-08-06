# Check whether BST contains Dead End :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/check-whether-bst-contains-dead-end/1)

<h3>
Given a Binary Search Tree that contains unique positive integer values greater than 0. The task is to complete the function isDeadEnd which returns true if the BST contains a dead end else returns false. Here Dead End means a leaf node, at which no other node can be inserted.<br><br>

Example 1:<br>
Input :   <br>
               8<br>
             /   \ <br>
           5      9<br>
         /  \     <br>
        2    7 <br>
       /<br>
      1     <br>
          
Output : <br>
Yes<br>
Explanation : 
Node 1 is a Dead End in the given BST.<br><br>
Example 2:<br>

Input :     <br>
              8<br>
            /   \ <br>
           7     10<br>
         /      /   \<br>
        2      9     13<br>

Output : <br>
Yes<br>
Explanation : 
Node 9 is a Dead End in the given BST.<br><br>
Your Task: You don't have to input or print anything. Complete the function isDeadEnd() which takes BST as input and returns a boolean value.<br><br>

Expected Time Complexity: O(N), where N is the number of nodes in the BST.<br>
Expected Space Complexity: O(N)<br>

Constraints:<br><br>
1 <= N <= 1001<br>
1 <= Value of Nodes <= 10001<br><br>
  
</h3>

***Solution***

```

class Solution{
  public:
    bool helper(Node* root,set<int>st)
    {
        if(root==NULL) return false;
        if(root->left==NULL && root->right==NULL)
        {
            if(st.find(root->data-1)!=st.end() && st.find(root->data+1)!=st.end()) 
                return true;
        }
        st.insert(root->data);
      return helper(root->left,st) || helper(root->right,st);
    
    }
    bool isDeadEnd(Node *root)
    {
        set<int>st;
        st.insert(0);
        return helper(root,st);
        
    }
};

```
