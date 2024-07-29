# Middle of the Linked List :-

[Problem Link] :--- (https://leetcode.com/problems/middle-of-the-linked-list/description/)

<h3>
Given the head of a singly linked list, return the middle node of the linked list.
<br><br>
If there are two middle nodes, return the second middle node.

<br><br>

Example 1:<br>
Input: head = [1,2,3,4,5]<br>
Output: [3,4,5]<br>
Explanation: The middle node of the list is node 3.<br><br>
Example 2:<br>
Input: head = [1,2,3,4,5,6]<br>
Output: [4,5,6]<br>
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.<br><br>
 
Constraints:<br><br>
The number of nodes in the list is in the range [1, 100].<br>
1 <= Node.val <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* slowPointer = head;
        ListNode* fastPointer = head;

        while (fastPointer != nullptr && fastPointer->next != nullptr) {
            slowPointer = slowPointer->next;
            fastPointer = fastPointer->next->next;
        }

        return slowPointer;
    }
};

```
