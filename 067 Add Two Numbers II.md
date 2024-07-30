# Add Two Numbers II :-

[Problem Link] :--- (https://leetcode.com/problems/add-two-numbers-ii/description/)

<h3>
You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.
<br><br>
You may assume the two numbers do not contain any leading zero, except the number 0 itself.<br><br>

Example 1:<br>
Input: l1 = [7,2,4,3], l2 = [5,6,4]<br>
Output: [7,8,0,7]<br><br>
Example 2:<br>
Input: l1 = [2,4,3], l2 = [5,6,4]<br>
Output: [8,0,7]<br><br>
Example 3:<br>
Input: l1 = [0], l2 = [0]<br>
Output: [0]<br><br>
 
Constraints:<br><br>

The number of nodes in each linked list is in the range [1, 100].<br>
0 <= Node.val <= 9<br>
It is guaranteed that the list represents a number that does not have leading zeros.<br><br>
 

Follow up: Could you solve it without reversing the input lists?<br><br>
  
</h3>

***Solution***

```

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverse(ListNode* head){
        ListNode* prev= NULL;
        ListNode* curr= head;
        while (curr){
            ListNode* forward= curr->next;
            curr->next= prev;
            prev= curr;
            curr= forward;
        }
        return prev;
    }
    ListNode* add(ListNode* l1, ListNode* l2){
        ListNode* head= new ListNode(-1);
        ListNode* curr= head;
        int carry=0;
        while (l1!=NULL || l2!=NULL || carry>0){
            int v1=0, v2=0;
            if (l1)v1= l1->val;
            if (l2)v2= l2->val;
            int sum= v1+v2+carry;
            carry= sum/10;
            sum= sum%10;
            curr->next= new ListNode(sum);
            curr= curr->next;
            if (l1)l1= l1->next;
            if (l2)l2= l2->next;
        }
        head= head->next;
        return head;
    }
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        l1= reverse(l1);
        l2= reverse(l2);
        ListNode* ans= add(l1,l2);
        ans= reverse(ans);
        return ans;
    }
};

```
