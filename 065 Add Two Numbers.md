# Add Two Numbers :-

[Problem Link] :--- (https://leetcode.com/problems/add-two-numbers/description/)

<h3>
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
<br><br>
You may assume the two numbers do not contain any leading zero, except the number 0 itself.<br><br>

Example 1:<br>
Input: l1 = [2,4,3], l2 = [5,6,4]<br>
Output: [7,0,8]<br>
Explanation: 342 + 465 = 807.<br><br>
Example 2:<br>

Input: l1 = [0], l2 = [0]<br>
Output: [0]<br><br>
Example 3:<br>

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]<br>
Output: [8,9,9,9,0,0,0,1]<br><br>
 
Constraints:<br><br>
The number of nodes in each linked list is in the range [1, 100].<br>
0 <= Node.val <= 9<br>
It is guaranteed that the list represents a number that does not have leading zeros.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode();
        ListNode* res = dummy;
        int total = 0, carry = 0;

        while (l1 || l2 || carry) {
            total = carry;

            if (l1) {
                total += l1->val;
                l1 = l1->next;
            }
            if (l2) {
                total += l2->val;
                l2 = l2->next;
            }

            int num = total % 10;
            carry = total / 10;
            dummy->next = new ListNode(num);
            dummy = dummy->next;
        }

        return res->next;        
    }
};

```
