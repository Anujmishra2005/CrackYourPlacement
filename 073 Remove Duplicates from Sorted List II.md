# Remove Duplicates from Sorted List II :-

[Problem Link] :--- (https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

<h3>
Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well..<br><br>

Example 1:<br>
Input: head = [1,2,3,3,4,4,5]<br>
Output: [1,2,5]<br><br>
Example 2:<br>
Input: head = [1,1,1,2,3]<br>
Output: [2,3]<br><br>
 

Constraints:<br><br>

The number of nodes in the list is in the range [0, 300].<br>
-100 <= Node.val <= 100<br>
The list is guaranteed to be sorted in ascending order.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        map<int, int> mp;
        ListNode *p = head;
        while (p) {
            mp[p->val]++;
            p = p->next;
        }
        
        ListNode *head2 = nullptr, *tail = nullptr;
        for (auto &it : mp) {
            if (it.second == 1) {
                ListNode *node = new ListNode(it.first);
                if (!head2) {
                    head2 = node;
                    tail = head2;
                } else {
                    tail->next = node;
                    tail = tail->next;
                }
            }
        }
        return head2;
    }
};

```
