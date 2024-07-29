# Convert Binary Number in a Linked List to Integer :-

[Problem Link] :--- (https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/description/)

<h3>
Given head which is a reference node to a singly-linked list. The value of each node in the linked list is either 0 or 1. The linked list holds the binary representation of a number.

Return the decimal value of the number in the linked list.

The most significant bit is at the head of the linked list.<br><br>

Example 1:<br>
Input: head = [1,0,1]<br>
Output: 5<br>
Explanation: (101) in base 2 = (5) in base 10<br><br>
Example 2:<br>
Input: head = [0]<br>
Output: 0<br><br>
 
Constraints:<br><br>
The Linked List is not empty.<br>
Number of nodes will not exceed 30.<br>
Each node's value is either 0 or 1.<br>
  
</h3>

***Solution***

```

class Solution {
public:
    int getDecimalValue(ListNode* head) {
        string num;
        while(head!=NULL){
            num+=to_string(head->val);
            head=head->next;
        }
        int res=0,pv=1;
        for(int i=num.size()-1;i>=0;i--){
            res+=pv*(stoi(num.substr(i,1)));
            pv*=2;
        }
        return res;
    }
};

```
