# leet-day50

# Basic Calculator

This is a solution to the "Basic Calculator" problem on LeetCode.

## Problem Description

You are given a string `s` representing a valid expression. Your task is to implement a basic calculator to evaluate this expression and return the result.

### Constraints:
- 1 <= `s.length` <= 3 * 10^5
- `s` consists of digits, '+', '-', '(', ')', and ' '.
- `s` represents a valid expression.
- '+' is not used as a unary operation (i.e., "+1" and "+(2 + 3)" is invalid).
- '-' could be used as a unary operation (i.e., "-1" and "-(2 + 3)" is valid).
- There will be no two consecutive operators in the input.
- Every number and running calculation will fit in a signed 32-bit integer.

## Approach

The solution to this problem involves simulating the calculation process by iterating through the characters of the input string `s`. We maintain two stacks: one for operands and one for operators.

1. Initialize two stacks: one for operands (`operands`) and another for operators (`operators`).

2. Initialize `result` to 0, `num` to 0 (to store the current operand), and `sign` to 1 (1 for positive, -1 for negative).

3. Loop through each character `c` in the input string `s`:

   - If `c` is a digit:
     - Update `num` by appending the digit to it.
   - If `c` is a '+' or '-':
     - Add the current `num` to `result` with the appropriate sign (`sign`).
     - Reset `num` to 0 and update `sign` accordingly.
   - If `c` is an opening parenthesis '(':
     - Push the current `result` and `sign` onto their respective stacks.
     - Reset `result` to 0 and `sign` to 1.
   - If `c` is a closing parenthesis ')':
     - Add the current `num` to `result` with the appropriate sign (`sign`).
     - Reset `num` to 0.
     - Multiply `result` by the last `sign` from the `operators` stack.
     - Add the result to the last `result` from the `operands` stack.
     - Pop the last `sign` from the `operators` stack.
     - Pop the last `result` from the `operands` stack.
   - Ignore spaces.

4. After the loop, add the final `num` to `result` with the appropriate sign.

5. Return the `result` as the final calculated value.

## Example

Input: s = "(1+(4+5+2)-3)+(6+8)"
Output: 23

## Time and Space Complexity

- Time Complexity: The algorithm iterates through each character of the input string once, so the time complexity is O(n), where n is the length of the input string.

- Space Complexity: The space complexity is O(n) because of the two stacks used to store operands and operators.

---
