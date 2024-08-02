# Rotten Oranges :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/rotten-oranges2536/1)

<h3>
Given a grid of dimension nxm where each cell in the grid can have values 0, 1 or 2 which has the following meaning:<br>
0 : Empty cell<br>
1 : Cells have fresh oranges<br>
2 : Cells have rotten oranges<br>
<br><br>
We have to determine what is the earliest time after which all the oranges are rotten. A rotten orange at index [i,j] can rot other fresh orange at indexes [i-1,j], [i+1,j], [i,j-1], [i,j+1] (up, down, left and right) in unit time. <br><br>

Example 1:<br>
Input: grid = {{0,1,2},{0,1,2},{2,1,1}}<br>
Output: 1<br>
Explanation: The grid is-<br>
0 1 2<br>
0 1 2<br>
2 1 1<br>
Oranges at positions (0,2), (1,2), (2,0)<br>
will rot oranges at (0,1), (1,1), (2,2) and <br>
(2,1) in unit time.<br><br>
Example 2:<br>

Input: grid = {{2,2,0,1}}<br>
Output: -1<br>
Explanation: The grid is-<br>
2 2 0 1<br>
Oranges at (0,0) and (0,1) can't rot orange at<br>
(0,3).<br><br>
 

Your Task:<br><br>
You don't need to read or print anything, Your task is to complete the function orangesRotting() which takes grid as input parameter and returns the minimum time to rot all the fresh oranges. If not possible returns -1.<br><br>
 

Expected Time Complexity: O(n*m)<br>
Expected Auxiliary Space: O(n*m)<br><br>
 

Constraints:<br><br>
1 ≤ n, m ≤ 500<br><br>
  
</h3>

***Solution***

```

class Solution 
{
    public:
    //Function to find minimum time required to rot all oranges. 
    int orangesRotting(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        queue<pair<pair<int,int>,int>>q;
        int vis[n][m];
        for(int i=0;i<n;i++) {
            for(int j=0;j<m;j++) {
                if(grid[i][j]==2) {
                    q.push({{i,j},0});
                    vis[i][j] = 2;
                }
                else {
                    vis[i][j] = 0;
                }
            }
        }
        int tm = 0;
        int dr[] = {-1,0,+1,0};
        int dc[] = {0,+1,0,-1};
        while(!q.empty()) {
            int r = q.front().first.first;
            int c = q.front().first.second;
            int t = q.front().second;
            q.pop();
            tm = max(tm,t);
            for(int i=0;i<4;i++) {
                int nrow = r+dr[i];
                int ncol = c+dc[i];
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && vis[nrow][ncol]!=2 && grid[nrow][ncol]==1) {
                    q.push({{nrow,ncol},t+1});
                    vis[nrow][ncol] = 2;
                }
            }
        }
        
        for(int i=0;i<n;i++) {
            for(int j=0;j<m;j++) {
                if(vis[i][j]!=2 && grid[i][j]==1) {
                    return -1;
                }
            }
        }
        return tm;
    }
};

```
