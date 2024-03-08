![Hadi-Banner](../hadi-banner.png)

# Solidity Topics

### Topics

- [Visibility](#visibility)
- [Reserved Keywords](#reserved-keywords)
- [Mutability]
- [Data Type](#data-type)
    - [Value Type](#value-type)
    - [Reference Type](#reference-type)
    - [Mapping Type](#mapping-type)
    - [Operator Type](#operator-type)

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


## Reserved Keywords
These keywords are reserved in Solidity. They might become part of the syntax in the future:

```after```, ```alias```, ```apply```, ```auto```, ```byte```, ```case```, ```copyof```, ```default```, ```define```, ```final```, ```implements```, ```in```, ```inline```, ```let```, ```macro```, ```match```, ```mutable```, ```null```, ```of```, ```partial```, ```promise```, ```reference```, ```relocatable```, ```sealed```, ```sizeof```, ``static``, ```supports```, ```switch```, ```typedef```, ```typeof```, ```var```.


## Mutability
- **```pure```**: The `pure` specifier indicates that a function does not read or modify the contract’s state. It is entirely deterministic and solely operates on its input parameters. This specifier is useful for functions that perform complex computations or transformations without interacting with the blockchain.
- **```view```**: The `view` specifier denotes that a function does not modify the contract’s state but can read from it. This is a read-only function and is commonly used for querying data from the blockchain. It is a cost-effective way to retrieve information without incurring gas fees.


## Data Type
Solidity is a statically typed language, which means that the type of each variable (state and local) needs to be specified. Solidity provides several elementary types which can be combined to form complex types.

In addition, types can interact with each other in expressions containing operators. For a quick reference of the various operators, see Order of Precedence of Operators.

The concept of “undefined” or “null” values does not exist in Solidity, but newly declared variables always have a default value dependent on its type. To handle any unexpected values, you should use the revert function to revert the whole transaction, or return a tuple with a second bool value denoting success.
### Value Type
The following are called value types because their variables will always be passed by value, i.e. they are always copied when they are used as function arguments or in assignments.
- **```bool```**: The possible values are constants ```true``` and ```false```.
- **```int```** / **```uint```**: Signed and unsigned integers of various sizes. Keywords ```uint8``` to ```uint256``` in steps of 8 (unsigned of 8 up to 256 bits) and ```int8``` to ```int256```. uint and int are aliases for ```uint256``` and ```int256```, respectively.
- **```fixed```** / **```ufixed```**: Signed and unsigned fixed point number of various sizes. Keywords ```ufixedMxN``` and ```fixedMxN```, where ```M``` represents the number of bits taken by the type and ```N``` represents how many decimal points are available. ```M``` must be divisible by 8 and goes from 8 to 256 bits. ```N``` must be between 0 and 80, inclusive. ```ufixed``` and fixed are aliases for ```ufixed128x18``` and ```fixed128x18```, respectively.
- Address: The address type comes in two largely identical flavors:
    - ```address```: Holds a 20 byte value (size of an Ethereum address).
    - ```address payable```: Same as address, but with the additional members ```transfer``` and ```send```.

    The idea behind this distinction is that ```address payable``` is an address you can send Ether to, while you are not supposed to send Ether to a plain ```address```, for example because it might be a smart contract that was not built to accept Ether.

    Members of Addresses:
    - ```balance``` and ```transfer```: It is possible to query the balance of an address using the property ```balance``` and to send Ether (in units of wei) to a payable address using the ```transfer``` function:

        ``` sol
        address payable x = payable(0x123);
        address myAddress = address(this);
        if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10);
        ```
        The ```transfer``` function fails if the balance of the current contract is not large enough or if the Ether transfer is rejected by the receiving account. The ```transfer``` function reverts on failure.
    
    - ```send```: send is the low-level counterpart of ```transfer```. If the execution fails, the current contract will not stop with an exception, but send will return false.
    - ```call```, ```delegatecall``` and ```staticcall```: n order to interface with contracts that do not adhere to the ABI, or to get more direct control over the encoding, the functions call, delegatecall and staticcall are provided. They all take a single bytes memory parameter and return the success condition (as a bool) and the returned data (bytes memory). The functions abi.encode, abi.encodePacked, abi.encodeWithSelector and abi.encodeWithSignature can be used to encode structured data.
        ``` sol
        bytes memory payload = abi.encodeWithSignature("register(string)", "MyName");
        (bool success, bytes memory returnData) = address(nameReg).call(payload);
        require(success);
        ```
    - ```code``` and ```codehash```: You can query the deployed code for any smart contract. Use .code to get the EVM bytecode as a bytes memory, which might be empty. Use .codehash to get the Keccak-256 hash of that code (as a bytes32). Note that addr.codehash is cheaper than using keccak256(addr.code).

### Reference Type
### Mapping Type
### Operator Type