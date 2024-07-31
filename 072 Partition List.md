# Partition List :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
Given the head of a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.
<br><br>
You should preserve the original relative order of the nodes in each of the two partitions.<br><br>

Example 1:<br>
Input: head = [1,4,3,2,5,2], x = 3<br>
Output: [1,2,2,4,3,5]<br><br>
Example 2:<br>
Input: head = [2,1], x = 2<br>
Output: [1,2]<br><br>
 

Constraints:<br><br>
The number of nodes in the list is in the range [0, 200].<br>
-100 <= Node.val <= 100<br>
-200 <= x <= 200<br><br>
  
</h3>

***Solution***

```
class Solution {
public:
    ListNode* partition(ListNode* head, int x) {
        if (!head || !head->next) return head;
        ListNode *list1 = nullptr, *tail1 = nullptr;    // List with val < x
        ListNode *list2 = nullptr, *tail2 = nullptr;    // List with val >= x
        ListNode *p = head;
        while (p) {
            ListNode *node = new ListNode(p->val);
            if (p->val < x) {
                if (!list1) {
                    list1 = node;
                    tail1 = list1;
                } else {
                    tail1->next = node;
                    tail1 = tail1->next;
                }
            } else {
                if (!list2) {
                    list2 = node;
                    tail2 = list2;
                } else {
                    tail2->next = node;
                    tail2 = tail2->next;
                }
            }
            p = p->next;
        }
        if (!list1) return list2;
        
        tail1->next = list2;
        return list1;
    }
};

```
