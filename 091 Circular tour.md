# Circular tour :-

[Problem Link] :--- (https://www.geeksforgeeks.org/problems/circular-tour-1587115620/1)

<h3>
Suppose there is a circle. There are N petrol pumps on that circle. You will be given two sets of data.<br>
1. The amount of petrol that every petrol pump has.<br>
2. Distance from that petrol pump to the next petrol pump.<br>
Find a starting point where the truck can start to get through the complete circle without exhausting its petrol in between.<br>
Note :  Assume for 1 litre petrol, the truck can go 1 unit of distance.<br><br>

Example 1:<br>
Input:<br>
N = 4<br>
Petrol = 4 6 7 4<br>
Distance = 6 5 3 5<br>
Output: 1<br>
Explanation: There are 4 petrol pumps with
amount of petrol and distance to next
petrol pump value pairs as {4, 6}, {6, 5},
{7, 3} and {4, 5}. The first point from
where truck can make a circular tour is
2nd petrol pump. Output in this case is 1
(index of 2nd petrol pump).<br>
Your Task:<br><br>
Your task is to complete the function tour() which takes the required data as inputs and returns an integer denoting a point from where a truck will be able to complete the circle (The truck will stop at each petrol pump and it has infinite capacity). If there exists multiple such starting points, then the function must return the first one out of those. (return -1 otherwise)
<br><br>
Expected Time Complexity: O(N)<br>
Expected Auxiliary Space : O(1)<br><br>

Constraints:<br>
2 ≤ N ≤ 10000<br>
1 ≤ petrol, distance ≤ 1000<br><br>
  
</h3>

***Solution***

```

class Solution{
  public:
  
    //Function to find starting point where the truck can start to get through
    //the complete circle without exhausting its petrol in between.
    int tour(petrolPump p[],int n)
    {
       //Your code here
        long long int s=0;
        for(int i=0;i<n;i++){
            s+=(p[i].petrol - p[i].distance);
        }
        if(s<0)
            return -1;
    
        //kadane's
        int index=0;
        int c=0;
        for(int i=0;i<n;i++){
            c+=(p[i].petrol - p[i].distance);
            if(c<0){
                c=0;
                index=i+1;
                
            }
            
        }
        return index;
        
    }

};;

```
