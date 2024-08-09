# BFS of graph :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

<h3>
Given a directed graph. The task is to do Breadth First Traversal of this graph starting from 0.<br><br>
Note: One can move from node u to node v only if there's an edge from u to v. Find the BFS traversal of the graph starting from the 0th vertex, from left to right according to the input graph. Also, you should only take nodes directly or indirectly connected from Node 0 in consideration.<br><br>

Example 1:<br>
Input:<br>
V = 5, E = 4<br>
adj = {{1,2,3},{},{4},{},{}}<br>


Output: <br>
0 1 2 3 4<br>
Explanation: <br>
0 is connected to 1 , 2 , 3.<br>
2 is connected to 4.<br>
so starting from 0, it will go to 1 then 2<br>
then 3. After this 2 to 4, thus bfs will be<br>
0 1 2 3 4.<br><br>
Example 2:<br>

Input:<br>
V = 3, E = 2<br>
adj = {{1,2},{},{}}<br>

Output: <br>
0 1 2<br>
Explanation:<br>
0 is connected to 1 , 2.<br>
so starting from 0, it will go to 1 then 2,<br>
thus bfs will be 0 1 2. <br><br>

Your task:<br><br>
You dont need to read input or print anything. Your task is to complete the function bfsOfGraph() which takes the integer V denoting the number of vertices and adjacency list as input parameters and returns  a list containing the BFS traversal of the graph starting from the 0th vertex from left to right.<br><br>


Expected Time Complexity: O(V + E)<br>
Expected Auxiliary Space: O(V)<br><br>


Constraints:<br><br>
1 ≤ V, E ≤ 104<br><br>
  
</h3>

***Solution***

```

class Solution {
  public:
    // Function to return Breadth First Traversal of given graph.
    vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        vector<int>solution;
        queue<int>q;
        q.push(0);
        vector<bool>vis(V,false);
        vis[0]=true;
        while(!q.empty())
        {
            int node = q.front();
            q.pop();
            solution.push_back(node);
            
            for(int a :adj[node])
            {
                if(!vis[a])
                {
                    q.push(a);
                    vis[a]=true;
                }
            }
        }
        return solution;
    }
};

```
