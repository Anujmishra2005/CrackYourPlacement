# Flatten a Multilevel Doubly Linked List :-

[Problem Link] :--- (https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/description/)

<h3>
You are given a doubly linked list, which contains nodes that have a next pointer, a previous pointer, and an additional child pointer. This child pointer may or may not point to a separate doubly linked list, also containing these special nodes. These child lists may have one or more children of their own, and so on, to produce a multilevel data structure as shown in the example below.
<br><br>
Given the head of the first level of the list, flatten the list so that all the nodes appear in a single-level, doubly linked list. Let curr be a node with a child list. The nodes in the child list should appear after curr and before curr.next in the flattened list.
<br><br>
Return the head of the flattened list. The nodes in the list must have all of their child pointers set to null.<br><br>

Example 1:<br>
Input: head = [1,2,3,4,5,6,null,null,null,7,8,9,10,null,null,11,12]<br>
Output: [1,2,3,7,8,11,12,9,10,4,5,6]<br>
Explanation: The multilevel linked list in the input is shown.<br>
After flattening the multilevel linked list it becomes:<br><br>

Example 2:<br>
Input: head = [1,2,null,3]<br>
Output: [1,3,2]<br>
Explanation: The multilevel linked list in the input is shown.<br>
After flattening the multilevel linked list it becomes:<br><br>

Example 3:<br>
Input: head = []<br>
Output: []<br>
Explanation: There could be empty list in the input.<br><br>
 

Constraints:<br><br>
The number of Nodes will not exceed 1000.<br>
1 <= Node.val <= 105<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    Node* flatten(Node* head) {
	for (Node* h = head; h; h = h->next)
	{
		if (h->child)
		{
			Node* next = h->next;
			h->next = h->child;
			h->next->prev = h;
			h->child = NULL;
			Node* p = h->next;
			while (p->next) p = p->next;
			p->next = next;
			if (next) next->prev = p;
		}
	}
	return head;
}
};

```
