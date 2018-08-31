# Design Pattern Decisions

## Commit/Reveal
No commit / reveal is needed, as non of the functionalities of the contract require this.

## Circuit Breaker/Emergency Stop
This is implemented in the contracts; The owner of the contract can halt the function of this contract (Mainly storing data and verifying data) if he/she desires.
However the get functions will still work.

## Pull Payments
No pull payments are required, as such it is not implemented in this contract.

## State Machine
The State Machine pattern is used to allow users to check the status of the verification process, since it is triggered by the Oracle, the verification process can be quite opaque.

## Fail early and fail loud
Most of the functions fail early, with the exception of the verifyIPFSHash function.
This is because the Oracle function needs to invoke the callback function of the contract; the gas estimate may not be enough. However we can still check the state of the Document to check if the function succeeds.

## Restricting Access
Certain functions are only restricted to the owner. This includes the circuit breaker and change owner functions.
By design, the other contract functions are allowed to be accessed by anyone: Anyone can store file data in the contract.

## Auto Deprecation
This is not implemented.

## Mortal
This is not implemented, as the data stored as proof of existence of files should not be able to be deleted at will. The contract owner should not have power to do so too.

## Speed Bump
This is not implemented, as it is not required.
