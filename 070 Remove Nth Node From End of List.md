# Remove Nth Node From End of List :-

[Problem Link] :--- (https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)

<h3>
Given the head of a linked list, remove the nth node from the end of the list and return its head.<br><br>

Example 1:<br>
Input: head = [1,2,3,4,5], n = 2<br>
Output: [1,2,3,5]<br><br>
Example 2:<br>

Input: head = [1], n = 1<br>
Output: []<br><br>
Example 3:<br>

Input: head = [1,2], n = 1<br>
Output: [1]<br><br>
 

Constraints:<br>

The number of nodes in the list is sz.<br>
1 <= sz <= 30<br>
0 <= Node.val <= 100<br>
1 <= n <= sz<br><br><br>

Follow up: Could you do this in one pass?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* res = new ListNode(0, head);
        ListNode* dummy = res;

        for (int i = 0; i < n; i++) {
            head = head->next;
        }

        while (head != nullptr) {
            head = head->next;
            dummy = dummy->next;
        }

        dummy->next = dummy->next->next;

        return res->next;        
    }
};

```
