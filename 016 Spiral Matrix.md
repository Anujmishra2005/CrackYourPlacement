# Spiral Matrix :-

[Problem Link] :--- (https://leetcode.com/problems/spiral-matrix/description/)

<h3>
Given an m x n matrix, return all elements of the matrix in spiral order.<br><br>

Example 1:<br>
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]<br>
Output: [1,2,3,6,9,8,7,4,5]<br><br>

Example 2:<br>
Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]<br>
Output: [1,2,3,4,8,12,11,10,9,5,6,7]<br><br>
 
Constraints:<br>
m == matrix.length<br>
n == matrix[i].length<br>
1 <= m, n <= 10<br>
-100 <= matrix[i][j] <= 100<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int l = 0, r = size(matrix[0]), t = 0, b = size(matrix);
        vector <int> res;
        while(l < r and t < b){
            for(int i = l; i < r ; i++) res.push_back(matrix[t][i]);
            t++;
            for(int i = t; i < b; i++) res.push_back(matrix[i][r-1]);
            r--;
            if(!(l < r and t < b)) break;
            for(int i = r-1; i >= l; i--) res.push_back(matrix[b-1][i]);
            b--;
            for(int i = b-1; i >= t; i--) res.push_back(matrix[i][l]);
            l++;
        }
        return res;
    }
};

```
