# Smallest Positive Missing :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1)

<h3>
You are given an array arr[] of N integers. The task is to find the smallest positive number missing from the array.
<br><br>
Note: Positive number starts from 1.<br><br>

Example 1:<br>
Input:<br>
N = 5<br>
arr[] = {1,2,3,4,5}<br>
Output: 6<br>
Explanation: Smallest positive missing number is 6.<br><br>
Example 2:<br>

Input:<br>
N = 5<br>
arr[] = {0,-10,1,3,-20}<br>
Output: 2<br>
Explanation: Smallest positive missing number is 2.<br><br>
Your Task:<br><br>
The task is to complete the function missingNumber() which returns the smallest positive missing number in the array.<br><br>

Expected Time Complexity: O(N).<br>
Expected Auxiliary Space: O(1).<br><br>
 
Constraints:<br><br>
1 <= N <= 106<br>
-106 <= arr[i] <= 106<br><br>
  
</h3>

***Solution***

```

class Solution {
public:
    // Function to find the smallest positive number missing from the array.
    int missingNumber(int arr[], int n) {
        // Separate positive numbers from non-positive numbers
        int j = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] > 0) {
                swap(arr[i], arr[j]);
                j++;
            }
        }

        // Mark presence of each positive number
        for (int i = 0; i < j; i++) {
            int num = abs(arr[i]);
            if (num - 1 < j && arr[num - 1] > 0) {
                arr[num - 1] = -arr[num - 1];
            }
        }

        // Find the first missing positive number
        for (int i = 0; i < j; i++) {
            if (arr[i] > 0) {
                return i + 1;
            }
        }

        // If all numbers from 1 to j are present, then the next missing number is j + 1
        return j + 1;
    }
};

```
