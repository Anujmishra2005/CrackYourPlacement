# Flood Fill :-

[Problem Link] :--- (https://leetcode.com/problems/flood-fill/description/)

<h3>
An image is represented by an m x n integer grid image where image[i][j] represents the pixel value of the image.
<br><br>
You are also given three integers sr, sc, and color. You should perform a flood fill on the image starting from the pixel image[sr][sc].
<br><br>
To perform a flood fill, consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with color.
<br><br>
Return the modified image after performing the flood fill.<br><br>

Example 1:<br>
Input: image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2<br>
Output: [[2,2,2],[2,2,0],[2,0,1]]<br>
Explanation: From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.<br>
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.<br><br>
Example 2:<br>

Input: image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, color = 0<br>
Output: [[0,0,0],[0,0,0]]<br>
Explanation: The starting pixel is already colored 0, so no changes are made to the image.<br><br>
 

Constraints:<br><br>

m == image.length<br>
n == image[i].length<br>
1 <= m, n <= 50<br>
0 <= image[i][j], color < 216<br>
0 <= sr < m<br>
0 <= sc < n<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    
    void dfs(vector<vector<int>>& image, int i, int j,int val, int newColor)
    {
        if(i<0 || i>=image.size() || j<0 || j>= image[0].size() || image[i][j] == newColor || image[i][j] != val)
        {
            return;
        }
        image[i][j] = newColor;
        dfs(image,i-1,j,val,newColor);
        dfs(image,i+1,j,val,newColor);
        dfs(image,i,j-1,val,newColor);
        dfs(image,i,j+1,val,newColor);
    }
    
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int newColor)
    {
        int val = image[sr][sc];
        dfs(image,sr,sc,val,newColor);
        return image;
    }
};

```
