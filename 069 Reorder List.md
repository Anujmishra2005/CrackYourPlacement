# Reorder List :-

[Problem Link] :--- (https://leetcode.com/problems/reorder-list/description/)

<h3>
You are given the head of a singly linked-list. The list can be represented as:
<br>
L0 → L1 → … → Ln - 1 → Ln<br>
Reorder the list to be on the following form:<br>

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …<br>
You may not modify the values in the list's nodes. Only nodes themselves may be changed..<br><br>

Example 1:<br>
Input: head = [1,2,3,4]<br>
Output: [1,4,2,3]<br><br>
Example 2:<br>
Input: head = [1,2,3,4,5]<br>
Output: [1,5,2,4,3]<br><br>

Constraints:<br><br>

The number of nodes in the list is in the range [1, 5 * 104].<br>
1 <= Node.val <= 1000<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    void reorderList(ListNode* head) {
        
        vector<ListNode*> temp;

        ListNode* curr = head;

        while(curr!=NULL)
        {
            temp.push_back(curr);

            curr = curr->next;
        }

        // for(auto i:temp) cout<<i->val<<" ";

        vector<ListNode*> vec;

        int i =0;
        int j = temp.size()-1;

        while(i<=j)
        {
            if(i==j)
            {
                vec.push_back(temp[i]);

                break;
            }
        
            vec.push_back(temp[i]);
            vec.push_back(temp[j]);

            i++;
            j--;
        }

        head -> next = NULL;

        curr = head;

        for(int i=1;i<vec.size();i++)
        {
            ListNode* t = new ListNode(vec[i]->val);

            curr -> next = t;

            curr = curr -> next;
        }
    }
};

```
