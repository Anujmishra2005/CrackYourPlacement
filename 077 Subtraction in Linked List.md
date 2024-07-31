# Subtraction in Linked List :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/subtraction-in-linked-list/1)

<h3>
You are given two linked lists that represent two large positive numbers. These two numbers are represented by the linked lists, subtract the smaller number from the larger one. Look at the examples to get a better understanding of the task.<br><br>

Example 1:<br>
Input:<br>
L1 = 1->0->0<br>
L2 = 1->2<br>
Output: 88<br>
Explanation:  <br>
First linked list represents 100 and the
second one represents 12. 12 subtracted from 100
gives us 88 as the result. It is represented
as 8->8 in the linked list.<br><br>
Example 2:<br>

Input:<br>
L1 = 0->0->6->3<br>
L2 = 7->1->0<br>
Output: 647<br>
Explanation: <br>
First linked list represents 0063 => 63 and 
the second one represents 710. 63 subtracted 
from 710 gives us 647 as the result. It is
represented as 6->4->7 in the linked list.<br><br>
Your Task:<br><br>
You do not have to take any input or print anything. The task is to complete the function subLinkedList() that takes heads of two linked lists as input parameters and which should subtract the smaller number from the larger one represented by the given linked lists and return the head of the linked list representing the result.
<br><br>
n and m are the lengths of the two linked lists respectively.<br>
Expected Time Complexity:  O(n+m)<br>
Expected Auxiliary Space: O(n+m)<br><br>

Constraints:<br><br>
1 <= n, m <= 10000<br>
0 <= values represented by the linked lists < 10n<br>
0 <= values represented by the linked lists < 10m<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    Node* subtract(Node* h1,Node* h2,bool borrow){
        if(!h1) return h1;
        if(borrow){
            h1->data--;
        }
        borrow=false;
        if(h2){
            if(h1->data<h2->data){
                h1->data+=10;
                borrow=true;
            }
            h1->data-=h2->data;
            h2=h2->next;
        }
        if(h1->data<0){
            h1->data+=10;
            borrow=true;
        }
        Node* ans=subtract(h1->next,h2,borrow);
        if(!ans) ans=h1;
        else{
            h1->next->next=h1;
        }
        return ans;
    }
    Node* revLinkedList(Node* root){
        if(!root->next) return root;
        Node* ans=revLinkedList(root->next);
        root->next->next=root;
        return ans;
    }
    void compare(Node* h1,Node* h2,int& valCompare,int& lenCompare){
        if(h1==NULL && h2==NULL) return;
        if(h1==NULL || h2==NULL){
            if(!h1) lenCompare=-1; else lenCompare=(1);
            return;
        }
        if(valCompare==0){
            if(h1->data>h2->data) valCompare=1;
            else if(h1->data<h2->data) valCompare=-1;
        }
        compare(h1->next,h2->next,valCompare,lenCompare);
        return;
    }
    Node* subLinkedList(Node* head1, Node* head2) {
        // Your implementation of subLinkedList goes here
        // Make sure to return the head of the resulting linked list
        while(head1->next && head1->data==0){
            head1=head1->next;
        }
        while(head2->next && head2->data==0){
            head2=head2->next;
        }
        Node* minuend=head1;
        Node* subtrahend=head2;
        int valCompare=0,lenCompare=0;
        compare(head1,head2,valCompare,lenCompare);
        if(lenCompare==-1 || (lenCompare==0 && valCompare==-1)){
            minuend=head2;
            subtrahend=head1;
        }
        Node* temp;
        temp=revLinkedList(minuend);
        minuend->next=NULL;
        minuend=temp;
        temp=revLinkedList(subtrahend);
        subtrahend->next=NULL;
        subtrahend=temp;
        temp=subtract(minuend,subtrahend,false);
        minuend->next=NULL;
        minuend=temp;
        while(minuend->next && minuend->data==0){
            minuend=minuend->next;
        }
        
        return minuend;
    }
};

```
