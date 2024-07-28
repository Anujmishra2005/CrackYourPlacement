# Count of Smaller Numbers After Self :-

[Problem Link] :--- (https://leetcode.com/problems/count-of-smaller-numbers-after-self/description/)

<h3>
Given an integer array nums, return an integer array counts where counts[i] is the number of smaller elements to the right of nums[i].<br><br>
Example 1:<br>
Input: nums = [5,2,6,1]<br>
Output: [2,1,1,0]<br>
Explanation:<br>
To the right of 5 there are 2 smaller elements (2 and 1).<br>
To the right of 2 there is only 1 smaller element (1).<br>
To the right of 6 there is 1 smaller element (1).<br>
To the right of 1 there is 0 smaller element.<br><br>
Example 2:<br>

Input: nums = [-1]<br>
Output: [0]<br><br>
Example 3:<br>

Input: nums = [-1,-1]<br>
Output: [0,0]<br><br>
 
Constraints:<br><br>
1 <= nums.length <= 105<br>
-104 <= nums[i] <= 104<br><br>
  
</h3>

***Solution***

```

class Solution {
public:

    struct Node{
        Node* links[2];
        int ct = 0;

        Node(){
            links[0] = links[1] = NULL;
            ct = 0;
        }
    };

    int countSmaller(Node* root, int x){
        Node* curr = root;
        bitset<15>bits(x);
        int ans = 0;
        for(int i = 14; i >= 0  && curr; i--){
            if(bits[i] == 1){

                if(curr -> links[0]){
                    ans += curr -> links[0] -> ct;
                    curr = curr -> links[1];
                }
                else curr = curr -> links[1];
            }
            else{

                curr = curr -> links[0];
            }
        }
        return ans;
    }

    void insert(Node* root, int x){
        Node* curr = root;
        bitset<15>bits(x);

        for(int i = 14; i >= 0; i--){
            if(!curr -> links[bits[i]]) curr -> links[bits[i]] = new Node();
            curr = curr -> links[bits[i]];
            curr -> ct ++;
        }
    }

    vector<int> countSmaller(vector<int>& nums) {
        
        int n = nums.size();

        vector<int>ans(n);
        Node* root = new Node();
        for(int i = n - 1; i >= 0; i--){
            ans[i] = countSmaller(root, (nums[i] + 1e4));
            insert(root, (nums[i] + 1e4) );
        }

        return ans;
    }
};

```
