# Palindrome Linked List :-

[Problem Link] :--- (https://leetcode.com/problems/palindrome-linked-list/description/)

<h3>
Given the head of a singly linked list, return true if it is a palindrome or false otherwise.<br><br>

Example 1:<br>
Input: head = [1,2,2,1]<br>
Output: true<br><br>
Example 2:<br>
Input: head = [1,2]<br>
Output: false<br><br>

Constraints:<br><br>
The number of nodes in the list is in the range [1, 105].<br>
0 <= Node.val <= 9<br><br>
 

Follow up: Could you do it in O(n) time and O(1) space?<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> listVals;
        while (head) {
            listVals.push_back(head->val);
            head = head->next;
        }
        
        int left = 0, right = listVals.size() - 1;
        while (left < right && listVals[left] == listVals[right]) {
            left++;
            right--;
        }
        return left >= right;
    }
};

```
