# Reverse Linked List :-

[Problem Link] :--- (https://leetcode.com/problems/reverse-linked-list/)

<h3>
Given the head of a singly linked list, reverse the list, and return the reversed list.<br><br>
Example 1:<br>
Input: head = [1,2,3,4,5]<br>
Output: [5,4,3,2,1]<br><br>
Example 2:<br>
Input: head = [1,2]<br>
Output: [2,1]<br><br>
Example 3:<br>
Input: head = []<br>
Output: []<br><br>
Constraints:<br><br>
The number of nodes in the list is the range [0, 5000].<br>
-5000 <= Node.val <= 5000<br><br>
 

Follow up: A linked list can be reversed either iteratively or recursively. Could you implement both?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* node = nullptr;

        while (head != nullptr) {
            ListNode* temp = head->next;
            head->next = node;
            node = head;
            head = temp;
        }

        return node;        
    }
};

```
