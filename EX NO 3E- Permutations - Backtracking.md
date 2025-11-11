
# EX 3E Generate Permutations using Backtracking  Approach.
## DATE: 13-10-2025
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

## Algorithm
1. Read the input array of numbers.
2. Use a recursive backtracking function that builds permutations by adding one number at a time.
3. At each step, skip numbers already included in the current temporary list.
4. When the temporary list reaches the length of the original array, add it to the result list.
5. Backtrack by removing the last added number and continue until all permutations are generated.

## Program:
```java
import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;

    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }

        for (int num : nums) {
            if (!curr.contains(num)) {
                curr.add(num);
                backtrack(curr, ans, nums);
                curr.remove(curr.size() - 1);
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }
        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}
```

## Output:
<img width="1122" height="108" alt="image" src="https://github.com/user-attachments/assets/cc0248a4-e0d0-4a72-abcc-47d91b0f5e1b" />



## Result:
The program successfully implemented and the expected output is verified.

```
Developed by: ASWIN B
Register Number:  212224110007
```
