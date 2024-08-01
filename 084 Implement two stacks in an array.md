# Implement two stacks in an array :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/implement-two-stacks-in-an-array/1)

<h3>
Your task is to implement  2 stacks in one array efficiently. You need to implement 4 methods.<br>
twoStacks : Initialize the data structures and variables to be used to implement  2 stacks in one array.<br>
push1 : pushes element into first stack.<br>
push2 : pushes element into second stack.<br>
pop1 : pops element from first stack and returns the popped element. If first stack is empty, it should return -1.<br>
pop2 : pops element from second stack and returns the popped element. If second stack is empty, it should return -1.<br><br>

Example 1:<br>
Input:<br>
push1(2)<br>
push1(3)<br>
push2(4)<br>
pop1()<br>
pop2()<br>
pop2()<br>
Output:<br>
3 4 -1<br>
Explanation:<br>
push1(2) the stack1 will be {2}<br>
push1(3) the stack1 will be {2,3}<br>
push2(4) the stack2 will be {4}<br>
pop1()   the poped element will be 3 from stack1 and stack1 will be {2}<br>
pop2()   the poped element will be 4 from stack2 and now stack2 is empty<br>
pop2()   the stack2 is now empty hence returned -1.<br><br>
Example 2:<br>

Input:<br>
push1(1)<br>
push2(2)<br>
pop1()<br>
push1(3)<br>
pop1()<br>
pop1()<br>
Output:<br>
1 3 -1<br>
Explanation:<br>
push1(1) the stack1 will be {1}<br>
push2(2) the stack2 will be {2}<br>
pop1()   the poped element will be 1 from stack1 and stack1 will be empty<br>
push1(3) the stack1 will be {3}<br>
pop1()   the poped element will be 3 from stack1 and stack1 will be empty<br>
pop1()   the stack1 is now empty hence returned -1.<br><br>
Your Task:<br><br>
You don't need to read input or print anything. You are required to complete the 4 methods push1, push2 which takes one argument an integer 'x' to be pushed into stack one and two and pop1, pop2 which returns the integer poped out from stack one and two. If no integer is present in the stack return -1.
<br><br>
Expected Time Complexity: O(1) for all the four methods.<br>
Expected Auxiliary Space: O(1) for all the four methods.<br><br>

Constraints:<br><br>
1 <= Number of queries <= 104<br>
1 <= Number of elements in the stack <= 100<br>
The sum of count of elements in both the stacks < size of the given array<br><br>
  
</h3>

***Solution***

```

class twoStacks {
  public:
        int a[10001];
        int top1;
        int top2;
      twoStacks() {
       top1=-1;
       top2=10001;    
      }

    // Function to push an integer into the stack1.
    void push1(int x) {
        if(top1<top2-1)
            a[++top1]=x;
        return;
        
    }

    // Function to push an integer into the stack2.
    void push2(int x) {
        if(top2>top1+1){
            a[--top2]=x;
        }
        return;
    }

    // Function to remove an element from top of the stack1.
    int pop1() {
        if(top1==-1)
            return(-1);
        return(a[top1--]);
        
    }

    // Function to remove an element from top of the stack2.
    int pop2() {
        if(top2==10001)
            return(-1);
        return(a[top2++]);
        
    }
};int pop2() {}
```
