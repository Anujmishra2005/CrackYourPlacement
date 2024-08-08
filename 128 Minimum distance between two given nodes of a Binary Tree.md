# Min distance between two given nodes of a Binary Tree :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/min-distance-between-two-given-nodes-of-a-binary-tree/1)

<h3>
Given a binary tree with n nodes and two node values, a and b, your task is to find the minimum distance between them. The given two nodes are guaranteed to be in the binary tree and all node values are unique.<br><br>

Example 1:<br>
Input:<br>
        1<br>
      /  \<br>
     2    3<br>
a = 2, b = 3<br>
Output: <br>
2<br>
Explanation: 
We need the distance between 2 and 3. Being at node 2, we need to take two steps ahead in order to reach node 3. The path followed will be: 2 -> 1 -> 3. Hence, the result is 2. <br><br>
Example 2:<br>

Input:<br>
        11<br>
      /   \<br>
     22  33<br>
    /  \  /  \<br>
  44 55 66 77<br>
a = 77, b = 22<br>
Output: <br>
3<br>
Explanation: 
We need the distance between 77 and 22. Being at node 77, we need to take three steps ahead in order to reach node 22. The path followed will be: 77 -> 33 -> 11 -> 22. Hence, the result is 3.<br><br>
Your Task:<br><br>
You don't need to read input or print anything. Your task is to complete the function findDist() which takes the root node of the tree and the two node values a and b as input parameters and returns the minimum distance between the nodes represented by the two given node values.<br><br>

Expected Time Complexity: O(n).<br>
Expected Auxiliary Space: O(Height of the Tree).<br><br>

Constraints:<br><br>
2 <= n <= 105<br>
0 <= Data of a node <= 109<br><br>
  
</h3>

***Solution***

```

class Solution{
    public:
    /* Should return minimum distance between a and b
    in a tree with given root*/
    int ans = 0;
    
    int f(Node* root, int a, int b, int i = 0){
        if(root == NULL) return 0;
        int l = f(root->left,a,b,i+1);
        int r = f(root->right,a,b,i+1);
        
        if((root->data == a || root->data == b) && (l||r)){
            ans = abs((max(l,r) - i));
            return (max(l,r) - i);
        }
        if(l && r){
            ans = abs(l+r - 2*i);
            return ans;
        }
        if(max(l,r)) return max(l,r);
        
        if(root->data == a) return i;
        else if(root->data == b) return i;
        else return 0;
        
    }
    
    int findDist(Node* root, int a, int b) {
        // Your code here
        f(root,a,b);
        return ans;
        
    }
};

```
