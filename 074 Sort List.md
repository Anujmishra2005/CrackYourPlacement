# Sort List :-

[Problem Link] :--- (https://leetcode.com/problems/sort-list/description/)

<h3>
Given the head of a linked list, return the list after sorting it in ascending order.<br><br>

Example 1:<br>
Input: head = [4,2,1,3]<br>
Output: [1,2,3,4]<br><br>
Example 2:<br>
Input: head = [-1,5,3,4,0]<br>
Output: [-1,0,3,4,5]<br><br>
Example 3:<br>
Input: head = []<br>
Output: []<br><br>
 

Constraints:<br><br>

The number of nodes in the list is in the range [0, 5 * 104].<br>
-105 <= Node.val <= 105<br><br>
 

Follow up: Can you sort the linked list in O(n logn) time and O(1) memory (i.e. constant space)?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* sortList(ListNode* head) {
        vector<int> sortable;

        ListNode *temp = head;
        while (temp != nullptr) {
            sortable.push_back(temp -> val);
            temp = temp -> next;
        }

        sort(sortable.begin(), sortable.end());

        temp = head;
        int i = 0;
        while (temp != nullptr) {
            temp -> val = sortable[i++];
            temp = temp -> next;
        }

        return head;
    }
};

```
