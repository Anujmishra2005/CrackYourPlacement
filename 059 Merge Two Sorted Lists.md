# Merge Two Sorted Lists :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.<br><br>

Example 1:<br>
Input: list1 = [1,2,4], list2 = [1,3,4]<br>
Output: [1,1,2,3,4,4]<br><br>
Example 2:<br>
Input: list1 = [], list2 = []<br>
Output: []<br><br>
Example 3:<br>
Input: list1 = [], list2 = [0]<br>
Output: [0]<br>
 
Constraints:<br><br>
The number of nodes in both lists is in the range [0, 50].<br>
-100 <= Node.val <= 100<br>
Both list1 and list2 are sorted in non-decreasing order.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* dummy = new ListNode(0);
        ListNode* cur = dummy;

        while (list1 && list2) {
            if (list1->val > list2->val) {
                cur->next = list2;
                list2 = list2->next;
            } else {
                cur->next = list1;
                list1 = list1->next;
            }
            cur = cur->next;
        }

        cur->next = list1 ? list1 : list2;

        return dummy->next;        
    }
};

```
