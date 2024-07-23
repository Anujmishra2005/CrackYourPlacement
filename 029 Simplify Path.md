# Simplify Path :-

[Problem Link] :--- (https://leetcode.com/problems/simplify-path/description/)

<h3>
Given an absolute path for a Unix-style file system, which begins with a slash '/', transform this path into its simplified canonical path.

In Unix-style file system context, a single period '.' signifies the current directory, a double period ".." denotes moving up one directory level, and multiple slashes such as "//" are interpreted as a single slash. In this problem, treat sequences of periods not covered by the previous rules (like "...") as valid names for files or directories.

The simplified canonical path should adhere to the following rules:

It must start with a single slash '/'.
Directories within the path should be separated by only one slash '/'.
It should not end with a slash '/', unless it's the root directory.
It should exclude any single or double periods used to denote current or parent directories.
Return the new path.<br><br>

Example 1:<br>
Input: path = "/home/"<br>
Output: "/home"<br>
Explanation:<br>
The trailing slash should be removed.<br><br>

Example 2:<br>
Input: path = "/home//foo/"<br>
Output: "/home/foo"<br>
Explanation:<br>
Multiple consecutive slashes are replaced by a single one.<br><br>

Example 3:<br>
Input: path = "/home/user/Documents/../Pictures"<br>
Output: "/home/user/Pictures"<br>
Explanation:<br>
A double period ".." refers to the directory up a level.<br><br>

Example 4:<br>
Input: path = "/../"<br>
Output: "/"<br>
Explanation:<br>
Going one level up from the root directory is not possible.<br><br>

Example 5:<br>
Input: path = "/.../a/../b/c/../d/./"<br>
Output: "/.../b/d"<br>
Explanation:<br>
"..." is a valid name for a directory in this problem.<br><br>

 
Constraints:<br>
1 <= path.length <= 3000<br>
path consists of English letters, digits, period '.', slash '/' or '_'.<br>
path is a valid absolute Unix path.<br>
  
</h3>

***Solution***

```

class Solution {
public:
void buildAns(stack<string>&s, string&ans) {
    if(s.empty()) {
        return;
    }
    string minPath = s.top(); s.pop();
    buildAns(s, ans);
    ans += minPath;
}
    string simplifyPath(string path) {
        stack<string>s;
        int i= 0;
        while(i < path.size()) {
            int start = i;
            int end = i+1;
            while(end<path.size() && path[end] != '/'){
                ++end;
            }
            string minPath = path.substr(start, end-start);
            i = end;
            if(minPath =="/" || minPath == "/."){
                continue;
            }
            if(minPath != "/.."){
                s.push(minPath);
            }
            else if(!s.empty()){
                s.pop();
            }
        }
        string ans = s.empty() ? "/" : "";
        buildAns(s, ans);
        return ans;
    }
};

```
