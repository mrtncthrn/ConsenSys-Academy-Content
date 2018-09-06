// Design Pattern Decisions

// Contract Design Decisions
Comments are included within scripted contract contents. These comments include informational dialogue concerning used methods and property descriptors. The inclusion of these details allow others to gain insight into the specifics of contract creation and detail how the workflow included is informed by implicit attention to UI principles and blockchain security protocol.

// Events
Events are emitted for significant contract state changes that are useful for updating the DApp. This allows the DApp to efficiently access contract state changes (like when a listing is created, bought or cancelled) from the EVM transaction log. This eliminates the concern with exceeding block gas limit that would exist if we attempted to retrieve this directly from the contract using function calls. 

 // Withdrawal from Contracts
 The recommended method of sending funds after an effect is using the withdrawal pattern. Although the most intuitive method of sending Ether, as a result of an effect, is a direct send call, this is not recommended as it introduces a potential security risk. In this project if your answer is accepted you can then claim the bounty using the claimBounty function.

// Marketplace Contract
The central marketplace is managed by a group of administrators. Admins allow store
owners to add stores to the marketplace.
Responsible for storing information about the types of users including:
Admins, Store Owners, Shoppers
Instances of store contracts shall be deployed from the source folder. The use of mappings is intentionally applied to reduce potential instances of increased financial expense due to loops.

// Mortal/Kill
Used to destroy a contract using the destroyAndSend function from the OpenZeppelin Destructible library. It takes one parameter which is the address that will receive all of the funds that the contract currently holds.

// Store Contract
Store contracts are what users interact with when they purchase products.
Each store created in the marketplace is it's own Store contract instance. This makes sense due to stores having to hold Ether, and have special properties related to store ownership. This way, each instance is responsible for holding it's own ETH, which reduces the amount of ETH stored in a given contract.

// Other Patterns Included in Design

// The Circuit Breaker or Emergency Stop Pattern
Stops contract functionality. i.e. if a bug was found but can still allow certain function to continue. In my case I thought it would be good for storage to have a circuit breaker that stops any creation of new items/answers but still allows item owners to cancel and refund their bounties.

// Library Usage
The SafeMath Library contract from OpenZeppelin was used to prevent integer overflow attacks and conduct arithmetic safely in the Store contract.

// Withdrawal from Contracts
The recommended method of sending funds after an effect is using the withdrawal pattern. Although the most intuitive method of sending Ether, as a result of an effect, is a direct send call, this is not recommended as it introduces a potential security risk. In this project if your answer is accepted you can then claim the bounty using the claimBounty function.
