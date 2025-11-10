
# EX 3C Tug of War problem - Backtracking.
## DATE: 29-09-2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Calculate the total sum of all numbers in the array; if the total sum is odd, it's impossible to partition into two equal sums, so immediately return false.
2. If the total sum is even, calculate the required target sum for one subset, which is $S/2$.
3. In the recursive helper function, if the target sum remaining is zero, a valid subset has been found, so return true.
4. If the index is out of bounds or the remaining target sum drops below zero (i.e., we've overshot the target), return false.
5. At each element, make two recursive calls: a) include the current number and reduce the target by its value (target - nums[index]), or b) exclude the current number and keep the target the same; if either call returns true, propagate true up the call stack.  

## Program:
```java
import java.util.Scanner;

public class Solution {

    public boolean canPartition(int[] nums) {
        int total = 0;
        for (int num : nums) total += num;
        if (total % 2 != 0) return false;
        return canPartitionHelper(nums, 0, total / 2);
    }

    private boolean canPartitionHelper(int[] nums, int index, int target) {
        if (target == 0) return true;
        if (index >= nums.length || target < 0) return false;
        if (canPartitionHelper(nums, index + 1, target - nums[index])) return true;
        return canPartitionHelper(nums, index + 1, target);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}
```

## Output:
<img width="388" height="176" alt="image" src="https://github.com/user-attachments/assets/3bc51e7e-040b-4b6e-b4bd-399d9c02d7a5" />



## Result:
The program successfully implemented and the expected output is verified.

```
Developed by: ASWIN B
Register Number:  212224110007
```
