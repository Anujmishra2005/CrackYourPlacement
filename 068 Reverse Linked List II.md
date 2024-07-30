# Reverse Linked List II :-

[Problem Link] :--- (https://leetcode.com/problems/reverse-linked-list-ii/description/)

<h3>
Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list..<br><br>

Example 1:<br>
Input: head = [1,2,3,4,5], left = 2, right = 4<br>
Output: [1,4,3,2,5]<br><br>
Example 2:<br>

Input: head = [5], left = 1, right = 1<br>
Output: [5]<br>
 

Constraints:<br><br>

The number of nodes in the list is n.<br>
1 <= n <= 500<br>
-500 <= Node.val <= 500<br>
1 <= left <= right <= n<br>
 

Follow up: Could you do it in one pass?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
        if (!head || left == right) {
            return head;
        }

        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* prev = dummy;

        for (int i = 0; i < left - 1; i++) {
            prev = prev->next;
        }

        ListNode* cur = prev->next;

        for (int i = 0; i < right - left; i++) {
            ListNode* temp = cur->next;
            cur->next = temp->next;
            temp->next = prev->next;
            prev->next = temp;
        }

        return dummy->next;        
    }
};

```
