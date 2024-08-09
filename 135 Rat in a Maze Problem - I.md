# Rat in a Maze Problem - I :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

<h3>
Consider a rat placed at (0, 0) in a square matrix mat of order n* n. It has to reach the destination at (n - 1, n - 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are 'U'(up), 'D'(down), 'L' (left), 'R' (right). Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.<br><br>
Note: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell. In case of no path, return an empty list. The driver will output "-1" automatically.<br><br>

Examples:<br>
Input: mat[][] = [[1, 0, 0, 0],<br>
                [1, 1, 0, 1], <br>
                [1, 1, 0, 0],<br>
                [0, 1, 1, 1]]<br>
Output: DDRDRR DRDDRR<br>
Explanation: The rat can reach the destination at (3, 3) from (0, 0) by two paths - DRDDRR and DDRDRR, when printed in sorted order we get DDRDRR DRDDRR.<br>
Input: mat[][] = [[1, 0],<br>
                [1, 0]]<br>
Output: -1<br>
Explanation: No path exists and destination cell is blocked.<br>
Expected Time Complexity: O(3n^2)<br>
Expected Auxiliary Space: O(l * x)<br>
Here l = length of the path, x = number of paths.<br><br>

Constraints:<br><br>
2 ≤ n ≤ 5<br>
0 ≤ mat[i][j] ≤ 1<br><br>
  
</h3>

***Solution***

```

class Solution {
  public:
  
  void maze( vector <vector<int> > &arr,int r,int c,int row,int col,string &temp,vector <string> &ans,vector <vector <int> > &visit){
     if(r==row-1 && c==col-1){
        ans.push_back(temp);
        return;
     }


    //up direction
    if(r-1 >=0 && visit[r-1][c] ==0 && arr[r-1][c] == 1){
        visit[r-1][c] = 1;
        temp.push_back('U');
        maze(arr,r-1,c,row,col,temp,ans,visit);
        temp.pop_back();
        visit[r-1][c] = 0;
    }
    //down direction

    if(r+1 <row && visit[r+1][c] ==0 && arr[r+1][c] == 1){
        visit[r+1][c] = 1;
        temp.push_back('D');
        maze(arr,r+1,c,row,col,temp,ans,visit);
        temp.pop_back();
        visit[r+1][c] = 0;
    }
    //left
    if(c-1 >=0 && visit[r][c-1] ==0 && arr[r][c-1] == 1){
        visit[r][c-1] = 1;
        temp.push_back('L');
        maze(arr,r,c-1,row,col,temp,ans,visit);
        temp.pop_back();
        visit[r][c-1] = 0;
    }
    //right
    if(c+1 <col && visit[r][c+1] ==0 && arr[r][c+1] == 1){
        visit[r][c+1] = 1;
        temp.push_back('R');
        maze(arr,r,c+1,row,col,temp,ans,visit);
        temp.pop_back();
        visit[r][c+1] = 0;
    }
}

    vector<string> findPath(vector<vector<int>> &arr) {
        // Your code goes here
     int row = arr.size();
    int col = arr[0].size();
    string temp;
    vector <string> ans;
    vector <vector <int> > visit(row,(vector <int> (col,0)));

    if (arr[0][0] == 1 && arr[row - 1][col - 1] == 1) {
        visit[0][0] = 1;
        maze(arr, 0, 0, row, col, temp, ans, visit);
    }
    
    return ans;
    }
};

```
