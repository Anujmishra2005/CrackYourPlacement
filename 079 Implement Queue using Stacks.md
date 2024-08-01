# Implement Queue using Stacks :-

[Problem Link] :--- (https://leetcode.com/problems/implement-queue-using-stacks/description/)

<h3>
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).
<br><br>
Implement the MyQueue class:<br><br>

void push(int x) Pushes element x to the back of the queue.<br>
int pop() Removes the element from the front of the queue and returns it.<br>
int peek() Returns the element at the front of the queue.<br>
boolean empty() Returns true if the queue is empty, false otherwise.<br><br>
Notes:<br><br>

You must use only standard operations of a stack, which means only push to top, peek/pop from top, size, and is empty operations are valid.<br>
Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.<br><br>

Example 1:<br>
Input<br>
["MyQueue", "push", "push", "peek", "pop", "empty"]<br>
[[], [1], [2], [], [], []]<br>
Output<br>
[null, null, null, 1, 1, false]<br>

Explanation<br>
MyQueue myQueue = new MyQueue();<br>
myQueue.push(1); // queue is: [1]<br>
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)<br>
myQueue.peek(); // return 1<br>
myQueue.pop(); // return 1, queue is [2]<br>
myQueue.empty(); // return false<br><br>
 

Constraints:<br><br>

1 <= x <= 9<br>
At most 100 calls will be made to push, pop, peek, and empty.<br>
All the calls to pop and peek are valid.<br><br>
  
</h3>

***Solution***

```

#include <stack>

class MyQueue {
public:
    MyQueue() {}
    
    void push(int x) {
        stack1.push(x);
    }
    
    int pop() {
        if (stack2.empty()) {
            transferElements();
        }
        int front = stack2.top();
        stack2.pop();
        return front;
    }
    
    int peek() {
        if (stack2.empty()) {
            transferElements();
        }
        return stack2.top();
    }
    
    bool empty() {
        return stack1.empty() && stack2.empty();
    }

private:
    std::stack<int> stack1;
    std::stack<int> stack2;
    
    void transferElements() {
        while (!stack1.empty()) {
            stack2.push(stack1.top());
            stack1.pop();
        }
    }
};

```
