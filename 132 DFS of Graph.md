# DFS of Graph :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1)

<h3>
You are given a connected undirected graph. Perform a Depth First Traversal of the graph.<br><br>
Note: Use the recursive approach to find the DFS traversal of the graph starting from the 0th vertex from left to right according to the graph.<br><br>
Example 1:<br>

Input: V = 5 , adj = [[2,3,1] , [0], [0,4], [0], [2]]<br>

Output: 0 2 4 3 1<br>
Explanation: <br>
0 is connected to 2, 3, 1.<br>
1 is connected to 0.<br>
2 is connected to 0 and 4.<br>
3 is connected to 0.<br>
4 is connected to 2.<br>
so starting from 0, it will go to 2 then 4,<br>
and then 3 and 1.<br>
Thus dfs will be 0 2 4 3 1.<br><br>
Example 2:<br>

Input: V = 4, adj = [[1,3], [2,0], [1], [0]]<br>

Output: 0 1 2 3<br>
Explanation:<br>
0 is connected to 1 , 3.<br>
1 is connected to 0, 2. <br>
2 is connected to 1.<br>
3 is connected to 0. <br>
so starting from 0, it will go to 1 then 2<br>
then back to 0 then 0 to 3<br>
thus dfs will be 0 1 2 3. <br><br>

Your task:<br><br>
You don't need to read input or print anything. Your task is to complete the function dfsOfGraph() which takes the integer V denoting the number of vertices and adjacency list as input parameters and returns a list containing the DFS traversal of the graph starting from the 0th vertex from left to right according to the graph.<br><br>


Expected Time Complexity: O(V + E)<br>
Expected Auxiliary Space: O(V)<br><br>


Constraints:<br><br>
1 ≤ V, E ≤ 104<br><br>
</h3>

***Solution***

```

class Solution {
    private:
        void dfs(int node , vector<int> &list , vector<int> adj[] , int vis[]){
            vis[node] = 1 ;
            list.push_back(node) ;
            
            for(auto it: adj[node]){
                if(vis[it]==0){
                    dfs(it,list,adj,vis);   
                }
            }
        }
  public:
    // Function to return a list containing the DFS traversal of the graph.
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        int vis[V] ={0}; 
        vis[0] = 1 ; 
        int start =0 ; 
        vector<int> list ; 
        dfs(start, list, adj, vis); 
        return list;
    }

};

```
