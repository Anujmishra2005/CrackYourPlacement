# Flatten Nested List Iterator :-

[Problem Link] :--- (https://leetcode.com/problems/flatten-nested-list-iterator/description/)

<h3>
You are given a nested list of integers nestedList. Each element is either an integer or a list whose elements may also be integers or other lists. Implement an iterator to flatten it.
<br>
Implement the NestedIterator class:<br>

NestedIterator(List<NestedInteger> nestedList) Initializes the iterator with the nested list nestedList.<br>
int next() Returns the next integer in the nested list.<br>
boolean hasNext() Returns true if there are still some integers in the nested list and false otherwise.<br>
Your code will be tested with the following pseudocode:<br>

initialize iterator with nestedList<br>
res = []<br>
while iterator.hasNext()<br>
    append iterator.next() to the end of res<br>
return res<br>
If res matches the expected flattened list, then your code will be judged as correct.<br><br>

Example 1:<br>
Input: nestedList = [[1,1],2,[1,1]]<br>
Output: [1,1,2,1,1]<br>
Explanation: By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,1,2,1,1].<br><br>
Example 2:<br>

Input: nestedList = [1,[4,[6]]]<br>
Output: [1,4,6]<br>
Explanation: By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,4,6].<br><br>
 

Constraints:<br><br>

1 <= nestedList.length <= 500<br>
The values of the integers in the nested list is in the range [-106, 106].<br><br>
  
</h3>

***Solution***

```

class NestedIterator {
public:
    queue<int> q;
    NestedIterator(vector<NestedInteger> &nestedList) {
        NestedInteger n;
        unravel(nestedList, q, n);
    }
    
    void unravel(vector<NestedInteger> &nestedList, queue<int>& q, NestedInteger n){
        for (int i=0; i<nestedList.size(); i++){
            if (nestedList[i].isInteger()){
                q.push(nestedList[i].getInteger());
            }
            else{
                unravel(nestedList[i].getList(), q, n);
                
            }
        }
        return ;
    }
    
    int next() {
        int x = q.front();
        q.pop();
        return x;
        
    }
    
    bool hasNext() {
       return !q.empty();        
    }
};

```
