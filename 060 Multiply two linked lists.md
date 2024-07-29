# Multiply two linked lists :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/multiply-two-linked-lists/1)

<h3>
Given elements as nodes of the two singly linked lists. The task is to multiply these two linked lists, say L1 and L2.

Note: The output could be large take modulo 10^9+7.<br><br>

Examples :<br>
Input: LinkedList L1 : 3->2 , LinkedList L2 : 2<br>
Output: 64<br>
Explanation: <br>
Multiplication of 32 and 2 gives 64.<br>
Input: LinkedList L1: 1->0->0 , LinkedList L2 : 1->0<br>
Output: 1000<br>
Explanation: <br>
Multiplication of 100 and 10 gives 1000.<br><br>
Expected Time Complexity: O(max(n,m))<br>
Expected Auxilliary Space: O(1)<br>
where n is the size of L1 and m is the size of L2<br><br>


Constraints:<br><br>
1 <= number of nodes <= 105<br>
1 <= node->data <= 103<br><br>
  
</h3>

***Solution***

```

class solution {
  public:
    long long  multiplyTwoLists (Node* l1, Node* l2)
{
  //Your code here
  
    long long  a = 0;
    long long  b = 0;
    Node* t1 = l1;
    Node* t2 = l2;
    while(t1 || t2){
        if(t1 != NULL){
            a = (a*10)%1000000007 + t1->data;
            t1 = t1->next;
        }
        if(t2 != NULL){
            b = (b*10)%1000000007 + t2->data;
            t2 = t2->next;
        }
    }
    
    return (a*b)%1000000007;

}
};

```
