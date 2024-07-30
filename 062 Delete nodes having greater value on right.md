# Delete nodes having greater value on right :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/delete-nodes-having-greater-value-on-right/1)

<h3>
Given a singly linked list, remove all the nodes in the list which have any node on their right whose value is greater. (Not just immediate Right , but entire List on the Right)
<br><br>

Example 1:<br>
Input:<br>
LinkedList = 12->15->10->11->5->6->2->3<br>
Output: 15 11 6 3<br>
Explanation: Since, 12, 10, 5 and 2 are<br>
the elements which have greater elements
on the following nodes. So, after deleting
them, the linked list would like be 15,
11, 6, 3.<br><br>
Example 2<br>

Input:<br>
LinkedList = 10->20->30->40->50->60<br>
Output: 60<br>
Explanation: All the nodes except the last
node has a greater value node on its right,
so all the nodes except the last node must
be removed.<br><br>
Your Task:<br><br>
The task is to complete the function compute() which should modify the list as required and return the head of the modified linked list. <br>
The printing is done by the driver code,<br><br>

Expected Time Complexity: O(N)<br>
Expected Auxiliary Space: O(1)<br><br>

Constraints:<br><br>
1 ≤ size of linked list ≤ 105<br>
1 ≤ element of linked list ≤ 105<br><br>

Note: Try to solve the problem without using any extra space.<br><br>
  
</h3>

***Solution***

```

class Solution
{
    public:
    Node *compute(Node *head)
    {
        if(head->next==NULL)return head;
        vector<int> v;
        Node* a = head;
        while(a!=NULL)
        {
            v.push_back(a->data);
            a=a->next;
        }
        vector<int> st;
        for(int i=0;i<v.size();i++)
        {
            bool flag=false;
            for(int j=i+1;j<v.size();j++)
            {
                if(v[j]>v[i])
                {
                    flag=true;
                    break;
                }
            }
            if(!flag)
            {
                st.push_back(v[i]);
            }
        }
        
        Node* ans = new Node(st[0]);
        Node* b = ans;
        for(int i=1;i<st.size();i++)
        {
            b->next  = new Node(st[i]);
            b=b->next;
        }
        return ans;
        // your code goes here
    }
    
};

```
