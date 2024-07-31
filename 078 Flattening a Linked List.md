# Flattening a Linked List :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)

<h3>
Given a Linked List, where every node represents a sub-linked-list and contains two pointers:<br>
(i) a next pointer to the next node,<br>
(ii) a bottom pointer to a linked list where this node is head.<br>
Each of the sub-linked lists is in sorted order.<br>
Flatten the Link List so all the nodes appear in a single level while maintaining the sorted order.<br><br>

Note: The flattened list will be printed using the bottom pointer instead of the next pointer. Look at the printList() function in the driver code for more clarity.<br><br>
Examples:<br>
Input:<br>
Output:  5-> 7-> 8- > 10 -> 19-> 20-> 22-> 28-> 30-> 35-> 40-> 45-> 50.<br>
Explanation: The resultant linked lists has every node in a single level.(Note: | represents the bottom pointer.)<br><br>
Input:<br>
Output: 5-> 7-> 8-> 10-> 19-> 22-> 28-> 30-> 50<br>
Explanation: The resultant linked lists has every node in a single level.(Note: | represents the bottom pointer.)<br><br>
Note: In the output section of the above examples, the -> represents the bottom pointer.<br><br>

Expected Time Complexity: O(n * n * m)<br>
Expected Auxiliary Space: O(n)<br><br>

Constraints:<br><br>
0 <= number of nodes <= 50<br>
1 <= no. of nodes in sub-LinkesList(mi) <= 20<br>
1 <= node->data <= 103<br><br>
  
</h3>

***Solution***

```

class Solution {
  public:
    // Function which returns the  root of the flattened linked list.
    Node* merge(Node* l1, Node* l2)
    {
        Node* d1=new Node(-1);
        Node* res=d1;
        while(l1!=NULL and l2!=NULL)
        {
            if(l1->data>l2->data)
            {
                d1->bottom=l2;
                l2=l2->bottom;
            }
            else{
                d1->bottom=l1;
                l1=l1->bottom;
            }
            d1->next=NULL;
            d1=d1->bottom;
        }
        if(l1!=NULL)
        {
            d1->bottom=l1;
        }
        if(l2!=NULL)
        {
            d1->bottom=l2;
        }
        return res->bottom;
    }
    Node* mergehead(Node* node)
    {
        if(node==NULL or node->next==NULL)
        {
            return node;
        }
        Node* h=mergehead(node->next);
        return merge(node,h);
    }
    // Function which returns the  root of the flattened linked list.
    Node *flatten(Node *root) {
        // Your code here
        return mergehead(root);
    }
};

```
