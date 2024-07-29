# Remove Duplicates from Sorted List :-

[Problem Link] :--- (https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)

<h3>
Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.<br><br>


Example 1:<br>
Input: head = [1,1,2]<br>
Output: [1,2]<br><br>
Example 2:<br>
Input: head = [1,1,2,3,3]<br>
Output: [1,2,3]<br>
 
 
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
        if (!head) {
            return nullptr;
        }
        
        ListNode* temp = head;
        ListNode* temp2 = head->next;
        int last = head->val;
        
        while (temp2 != nullptr) { 
            if (temp2->val == last) { 
                if (temp2->next == nullptr) { 
                    temp->next = nullptr;
                    break;
                }
                temp2 = temp2->next; 
                temp->next = temp2; 
            } else { 
                temp = temp2;
                last = temp->val;
                temp2 = temp2->next;
            }
        }
        
        return head;
    }
};

```
