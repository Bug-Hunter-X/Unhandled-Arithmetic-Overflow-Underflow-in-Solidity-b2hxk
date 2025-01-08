# Unhandled Arithmetic Overflow/Underflow in Solidity

This repository demonstrates a common error in Solidity: unhandled arithmetic overflow and underflow.  The `myFunc` function performs division without any checks for zero division. This can lead to unexpected behavior or a runtime error if `b` is zero.

## Bug

The `bug.sol` file contains the problematic code:

```solidity
function myFunc(uint256 a, uint256 b) public pure returns (uint256) {
  unchecked {
    return a / b; 
  }
}
```

## Solution

The `bugSolution.sol` file shows the corrected code, incorporating checks to prevent errors:

```solidity
function myFunc(uint256 a, uint256 b) public pure returns (uint256) {
    require(b != 0, "Cannot divide by zero");
    return a / b;
}
```

This version adds a `require` statement to ensure that `b` is not zero. If `b` is zero, the transaction will revert, preventing the error.