# Permutations-on-a-given-string-using-recursion-in-javascript-


/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
    /**
     * Recursive function to find all permutations
     * @param {number[]} nums - The array to find permutations for
     * @param {number[][]} ans - The result array to store permutations
     * @param {number} index - The current index during recursion
     */
    const solve = function(nums, ans, index) {
        // Base case: if the current index is beyond the array length
        if (index >= nums.length) {
            ans.push([...nums]); // Clone the array to avoid reference issues
            return;
        }

        // Iterate through the array starting from the current index
        for (let j = index; j < nums.length; j++) {
            // Swap elements at the current index and j
            [nums[index], nums[j]] = [nums[j], nums[index]];
            
            // Recursively call solve for the next index
            solve(nums, ans, index + 1);
            
            // Backtrack by undoing the swap
            [nums[index], nums[j]] = [nums[j], nums[index]];
        }
    };

    // Initialize an empty array to store permutations
    let ans = [];

    // Start the permutation process from index 0
    let index = 0;

    // Call the solve function to find permutations
    solve(nums, ans, index);

    // Return the array containing all permutations
    return ans;
};

// Example usage:
let result = permute([1, 2, 3]);
console.log(result);

Approach:

The permute function uses a recursive approach to find all permutations of a given array (nums). The solve function is the recursive helper that swaps elements to generate permutations. Here's a step-by-step breakdown of the approach:

Base Case:

If the current index (index) is greater than or equal to the length of the array, push a clone of the array to the result array (ans). This is the base case that stops the recursion.
Iteration:

Iterate through the array starting from the current index (j = index).
Swap the elements at the current index and j using destructuring assignment.
Recursion:

Recursively call the solve function for the next index (index + 1).
Backtrack:

Undo the swap to backtrack and explore other possibilities.
Initialization and Return:

Initialize an empty array (ans) and the starting index (index = 0).
Call the solve function with the initial parameters.
Return the array containing all permutations (ans).
