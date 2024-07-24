# Rotate Image :-

[Problem Link] :--- (https://leetcode.com/problems/rotate-image/description/)

<h3>
You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).<br>
You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

 <br><br>

Example 1:<br>
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]<br>
Output: [[7,4,1],[8,5,2],[9,6,3]]<br><br>
Example 2:<br>
Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]<br>
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]<br><br>
 
Constraints:<br>
n == matrix.length == matrix[i].length<br>
1 <= n <= 20<br>
-1000 <= matrix[i][j] <= 1000<br>
  
</h3>

***Solution***

```

class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        int edgeLength = matrix.size();

        int top = 0;
        int bottom = edgeLength - 1;

        while (top < bottom) {
            for (int col = 0; col < edgeLength; col++) {
                int temp = matrix[top][col];
                matrix[top][col] = matrix[bottom][col];
                matrix[bottom][col] = temp;
            }
            top++;
            bottom--;
        }

        for (int row = 0; row < edgeLength; row++) {
            for (int col = row + 1; col < edgeLength; col++) {
                int temp = matrix[row][col];
                matrix[row][col] = matrix[col][row];
                matrix[col][row] = temp;
            }
        }        
    }
};
```
