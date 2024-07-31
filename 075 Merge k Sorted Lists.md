# Merge k Sorted Lists :-

[Problem Link] :--- (https://leetcode.com/problems/sort-colors/description/)

<h3>
You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.
<br><br>
Merge all the linked-lists into one sorted linked-list and return it<br><br>

Example 1:<br>
Input: lists = [[1,4,5],[1,3,4],[2,6]]<br>
Output: [1,1,2,3,4,4,5,6]<br>
Explanation: The linked-lists are:<br>
[
  1->4->5,
  1->3->4,
  2->6
]<br>
merging them into one sorted list:<br>
1->1->2->3->4->4->5->6<br><br>
Example 2:<br>

Input: lists = []<br>
Output: []<br><br>
Example 3:<br>

Input: lists = [[]]<br>
Output: []<br><br>
 

Constraints:<br><br>

k == lists.length<br>
0 <= k <= 104<br>
0 <= lists[i].length <= 500<br>
-104 <= lists[i][j] <= 104<br>
lists[i] is sorted in ascending order.<br>
The sum of lists[i].length will not exceed 104.<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (lists.empty()) {
            return nullptr;
        }
        return mergeKListsHelper(lists, 0, lists.size() - 1);
    }
    
    ListNode* mergeKListsHelper(vector<ListNode*>& lists, int start, int end) {
        if (start == end) {
            return lists[start];
        }
        if (start + 1 == end) {
            return merge(lists[start], lists[end]);
        }
        int mid = start + (end - start) / 2;
        ListNode* left = mergeKListsHelper(lists, start, mid);
        ListNode* right = mergeKListsHelper(lists, mid + 1, end);
        return merge(left, right);
    }
    
    ListNode* merge(ListNode* l1, ListNode* l2) {
        ListNode* dummy = new ListNode(0);
        ListNode* curr = dummy;
        
        while (l1 && l2) {
            if (l1->val < l2->val) {
                curr->next = l1;
                l1 = l1->next;
            } else {
                curr->next = l2;
                l2 = l2->next;
            }
            curr = curr->next;
        }
        
        curr->next = l1 ? l1 : l2;
        
        return dummy->next;
    }
};

```
