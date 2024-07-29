# Remove Linked List Elements :-

[Problem Link] :--- (https://leetcode.com/problems/remove-linked-list-elements/description/)

<h3>
Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.<br><br>

Example 1:<br>
Input: head = [1,2,6,3,4,5,6], val = 6<br>
Output: [1,2,3,4,5]<br><br>
Example 2:<br>
Input: head = [], val = 1<br>
Output: []<br><br>
Example 3:<br>
Input: head = [7,7,7,7], val = 7<br>
Output: []<br>
 
Constraints:<br><br>
The number of nodes in the list is in the range [0, 104].<br>
1 <= Node.val <= 50<br>
0 <= val <= 50<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* temp = head;
        ListNode* newHead = new ListNode(0);
        ListNode* newTemp = newHead;

        while(temp != NULL)
        {
            if(temp-> val != val)
            {
                newTemp-> next = new ListNode(temp-> val);
                newTemp = newTemp-> next;
            }
            temp = temp-> next;
        }
        return newHead-> next;
    }
};

```
