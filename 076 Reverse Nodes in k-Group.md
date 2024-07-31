# Reverse Nodes in k-Group :-

[Problem Link] :--- (https://leetcode.com/problems/reverse-nodes-in-k-group/description/)

<h3>
Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.
<br><br>
k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.
<br><br>
You may not alter the values in the list's nodes, only nodes themselves may be changed.<br><br>

Example 1:<br>
Input: head = [1,2,3,4,5], k = 2<br>
Output: [2,1,4,3,5]<br><br>
Example 2:<br>
Input: head = [1,2,3,4,5], k = 3<br>
Output: [3,2,1,4,5]<br>
 
Constraints:<br><br>
The number of nodes in the list is n.<br>
1 <= k <= n <= 5000<br>
0 <= Node.val <= 1000<br><br>
 

Follow-up: Can you solve the problem in O(1) extra memory space?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    int getlength(ListNode* head){
        ListNode* temp=head;
        int len=0;
        while(temp!=NULL){
            temp=temp->next;
            len++;
        }
        return len;
    }
    ListNode* reverseKGroup(ListNode* head, int k) {
        if(head==NULL || head->next==NULL){
            return head;
        }
        int len=getlength(head);
        if(len<k){
            return head;
        }
        int position=0;
        ListNode* prev=NULL;
        ListNode* curr=head;
        while(position<k){
            ListNode* forward=curr->next;
            curr->next=prev;
            prev=curr;
            curr=forward;
            position++;
        }
        if(curr!=NULL){
            ListNode* recursionhead=reverseKGroup(curr,k);
            head->next=recursionhead;
        }
        return prev;
    }
};

```
