# Implement Stack using Queues :-

[Problem Link] :--- (https://leetcode.com/problems/implement-stack-using-queues/description/)

<h3>
Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).
<br><br>
Implement the MyStack class:<br><br>

void push(int x) Pushes element x to the top of the stack.<br>
int pop() Removes the element on the top of the stack and returns it.<br>
int top() Returns the element on the top of the stack.<br>
boolean empty() Returns true if the stack is empty, false otherwise.<br><br>
Notes:<br><br>

You must use only standard operations of a queue, which means that only push to back, peek/pop from front, size and is empty operations are valid.<br>
Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.<br><br>

Example 1:<br>
Input<br>
["MyStack", "push", "push", "top", "pop", "empty"]<br>
[[], [1], [2], [], [], []]<br>
Output<br>
[null, null, null, 2, 2, false]<br>

Explanation<br>
MyStack myStack = new MyStack();<br>
myStack.push(1);<br>
myStack.push(2);<br>
myStack.top(); // return 2<br>
myStack.pop(); // return 2<br>
myStack.empty(); // return False<br><br>
 

Constraints:<br><br>

1 <= x <= 9<br>
At most 100 calls will be made to push, pop, top, and empty.<br>
All the calls to pop and top are valid.<br>
 

Follow-up: Can you implement the stack using only one queue?<br><br>
  
</h3>

***Solution***

```

class MyStack {
public:
    queue<int> que;

    MyStack() {
        
    }
    
    void push(int x) {
        que.push(x);
        int n = que.size(); 

        for(int i=0; i<n-1; i++){
            que.push(que.front());
            que.pop();
        }
    }
    
    int pop() {
        int result = que.front();
        que.pop();

        return result;
    }
    
    int top() {
        return que.front();
    }
    
    bool empty() {
        return que.empty();
    }
};

```
