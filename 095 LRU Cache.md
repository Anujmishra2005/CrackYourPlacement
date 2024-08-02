# LRU Cache :-

[Problem Link] :--- (https://leetcode.com/problems/lru-cache/description/)

<h3>
Design a data structure that follows the constraints of a Least Recently Used (LRU) cache.
<br><br>
Implement the LRUCache class:<br><br>

LRUCache(int capacity) Initialize the LRU cache with positive size capacity.<br>
int get(int key) Return the value of the key if the key exists, otherwise return -1.<br>
void put(int key, int value) Update the value of the key if the key exists. Otherwise, add the key-value pair to the cache. If the number of keys exceeds the capacity from this operation, evict the least recently used key.<br>
The functions get and put must each run in O(1) average time complexity.<br><br>

Example 1:<br>
Input<br>
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]<br>
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]<br>
Output<br>
[null, null, null, 1, null, -1, null, -1, 3, 4]<br>

Explanation<br>
LRUCache lRUCache = new LRUCache(2);<br>
lRUCache.put(1, 1); // cache is {1=1}<br>
lRUCache.put(2, 2); // cache is {1=1, 2=2}<br>
lRUCache.get(1);    // return 1<br>
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}<br>
lRUCache.get(2);    // returns -1 (not found)<br>
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}<br>
lRUCache.get(1);    // return -1 (not found)<br>
lRUCache.get(3);    // return 3<br>
lRUCache.get(4);    // return 4<br><br>
 

Constraints:<br><br>

1 <= capacity <= 3000<br>
0 <= key <= 104<br>
0 <= value <= 105<br>
At most 2 * 105 calls will be made to get and put.<br><br>
  
</h3>

***Solution***

```

class LRUCache {
public:
    inline static int M[10001];
    inline static int16_t L[10002][2];
    int cap, size = 0;
    const int NONE = 10001;
    int head = NONE, tail = NONE;
    
    LRUCache(int capacity) : cap(capacity) {
        memset(M, 0xff, sizeof M);
    }
    
    inline void erase(int key) {
        const int pre = L[key][0];
        const int nxt = L[key][1];
        L[pre][1] = nxt;
        L[nxt][0] = pre;
        if (head == key) head = nxt;
        if (tail == key) tail = pre;
    }
    
    inline void push_front(int key) {
        L[key][0] = NONE;
        L[key][1] = head;
        L[head][0] = key;
        head = key;
        if (tail == NONE)
            tail = key;
    }
    
    inline int pop_back() {
        int ret = tail;
        tail = L[tail][0];
        L[tail][1] = NONE;
        if (tail == NONE)
            head = NONE;
        return ret;
    }
    
    int get(int key) {
        if (M[key] == -1) return -1;
        erase(key);
        push_front(key);
        return M[key];
    }
    
    void put(int key, int value) {
        if (M[key] != -1) {
            erase(key);
        } else {
            if (size == cap) {
                int poped = pop_back();
                M[poped] = -1;
                size -= 1;
            }
            size += 1;
        }
        push_front(key);
        M[key] = value;
    }
};

```
