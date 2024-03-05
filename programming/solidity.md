![Hadi-Banner](../hadi-banner.png)

# Solidity Topics

### Topics

- [Visibility](#visibility)
- [Data Type](#data-type)

---

## Visibility
1. **public**: The public keyword means that the state variable or function is accessible from anywhere, both inside the contract and from external contracts.
    ``` sol 
    uint256 public myVariable;
    ```
2. **internal**: The internal keyword restricts access to within the current contract and any contracts that inherit from it. External contracts cannot access internal elements.
    ``` sol 
    uint256 public myVariable;
    ```
3. **external**: The external keyword is typically used for functions and means that the function can only be called from outside the contract. External functions cannot be called internally.
    ``` sol 
    function myFunction() external {
        // Function logic
    }
    ```
3. **private**: The private keyword restricts access to only within the current contract. It is the most restrictive visibility level.
    ``` sol 
   function privateFunction() private {
        // Function logic
    }
    ```


## Data Type