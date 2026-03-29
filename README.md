📌 Find Pairs with Sum = 0 (Two Pointer Approach)
🚀 Problem Statement

Given an array of integers, find all unique pairs such that:

arr[i] + arr[j] = 0

Return the result as a list of pairs.

🧠 Approach
✅ Step 1: Sort the Array
Sorting helps in applying the two-pointer technique
✅ Step 2: Use Two Pointers
lp (left pointer) → start of array
rp (right pointer) → end of array
✅ Step 3: Traverse
If sum == 0 → store pair
If sum < 0 → move lp++
If sum > 0 → move rp--
❗ Handling Duplicates

To avoid duplicate pairs:

int leftVal = arr[lp];
int rightVal = arr[rp];

while (lp < rp && arr[lp] == leftVal) lp++;
while (lp < rp && arr[rp] == rightVal) rp--;

👉 This ensures each pair is added only once

💻 Code Implementation
import java.util.*;

class Solution {
    public static ArrayList<ArrayList<Integer>> getPairs(int[] arr) {
        ArrayList<ArrayList<Integer>> result = new ArrayList<>();
        
        Arrays.sort(arr);
        
        int lp = 0, rp = arr.length - 1;
        
        while (lp < rp) {
            int sum = arr[lp] + arr[rp];
            
            if (sum == 0) {
                ArrayList<Integer> pair = new ArrayList<>();
                pair.add(arr[lp]);
                pair.add(arr[rp]);
                result.add(pair);
                
                int leftVal = arr[lp];
                int rightVal = arr[rp];
                
                // Skip duplicates
                while (lp < rp && arr[lp] == leftVal) lp++;
                while (lp < rp && arr[rp] == rightVal) rp--;
            } 
            else if (sum < 0) {
                lp++;
            } 
            else {
                rp--;
            }
        }
        
        return result;
    }
}
🧪 Example
Input
[9, 4, -2, -1, 5, 0, -5, -3, 2]
Sorted Array
[-5, -3, -2, -1, 0, 2, 4, 5, 9]
Output
[-5, 5]
[-2, 2]
⏱️ Complexity
Type	Complexity
Time	O(n log n) (sorting)
Space	O(1) (excluding result)

Author 
Sanjeev Sharma
