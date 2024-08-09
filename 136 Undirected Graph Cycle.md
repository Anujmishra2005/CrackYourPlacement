# Undirected Graph Cycle :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

<h3>
Given an undirected graph with V vertices labelled from 0 to V-1 and E edges, check whether it contains any cycle or not. Graph is in the form of adjacency list where adj[i] contains all the nodes ith node is having edge with.<br><br>

Example 1:<br>
Input:  <br>
V = 5, E = 5<br>
adj = {{1}, {0, 2, 4}, {1, 3}, {2, 4}, {1, 3}} <br>
Output: 1<br>
Explanation: <br>

1->2->3->4->1 is a cycle.<br><br>
Example 2:<br>

Input: <br>
V = 4, E = 2<br>
adj = {{}, {2}, {1, 3}, {2}}<br>
Output: 0<br>
Explanation: <br>

No cycle in the graph.<br><br>
 

Your Task:<br><br>
You don't need to read or print anything. Your task is to complete the function isCycle() which takes V denoting the number of vertices and adjacency list as input parameters and returns a boolean value denoting if the undirected graph contains any cycle or not, return 1 if a cycle is present else return 0.
<br><br>
NOTE: The adjacency list denotes the edges of the graph where edges[i] stores all other vertices to which ith vertex is connected.<br><br>

 

Expected Time Complexity: O(V + E)<br>
Expected Space Complexity: O(V)<br><br>


 

Constraints:<br><br>
1 ≤ V, E ≤ 105<br><br>
  
</h3>

***Solution***

```

class Solution {
  public:
    void dfs(vector<int> adj[], vector<int> &vis, int V, int node, int prev, bool &check) {
    vis[node] = 1;
    for (int i : adj[node]) {
        if (i == prev) {
            continue;
        } else if (vis[i]) {
            check = true;
        } else {
            dfs(adj, vis, V, i, node, check);
        }
    }
}

bool isCycle(int V, vector<int> adj[]) {
    vector<int> vis(V, 0);
    for (int i = 0; i < V; i++) {
        if (!vis[i]) {
            bool check = false;
            dfs(adj, vis, V, i, -1, check);
            if (check) {
                return true;
            }
        }
    }
    return false;
}

};

```
