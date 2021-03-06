# smart-contracts

## What is Smart-contracts

Smart contracts are the executable programs that run on the Ethereum blockchain. Smart contracts are written using specific programming languages that compile to EVM bytecode (low-level machine instructions called **opcodes**).

The two most active and maintained languages are:

-   Solidity
-   Vyper

Example contract 

```
// SPDX-License-Identifier: GPL-3.0
pragma solidity >= 0.7.0;

contract Coin {
    // The keyword "public" makes variables
    // accessible from other contracts
    address public minter;
    mapping (address => uint) public balances;

    // Events allow clients to react to specific
    // contract changes you declare
    event Sent(address from, address to, uint amount);

    // Constructor code is only run when the contract
    // is created
    constructor() {
        minter = msg.sender;
    }

    // Sends an amount of newly created coins to an address
    // Can only be called by the contract creator
    function mint(address receiver, uint amount) public {
        require(msg.sender == minter);
        require(amount < 1e60);
        balances[receiver] += amount;
    }

    // Sends an amount of existing coins
    // from any caller to an address
    function send(address receiver, uint amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

**Note** : The Application Binary Interface (ABI) Specifications define Operating System and Application interfaces that are neccesary to construct an execution environment for applications.

**Interact with Contracts on Networks **

- Ethererum
- 


## What Smart Contracts can do 

- Create forwarding contracts, such as a savings account that resends income to a separate bucket automatically
- Manage a relationship between several parties, such as a freelancer agreement or payroll
- Act as a software library for other contracts
- Act as controllers for other systems or sets of contracts
- Serve as application-specific logic for a communal web service
- Maintain an accounting system for something in the real world, or for other contracts
- Serve as a utility that developers can use on a single-serving basis, such as a random number generator

**gas**
Gas prices of all EVM operations: https://docs.google.com/spreadsheets/d/1m89CVujrQe5LAFJ8-YAUCcNK950dUzMQPMJBxRtGCqs/edit#gid=0

**ABI**

https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI#functions

**DAPPS**

Dapps with Meteor.js: https://github.com/ethereum/wiki/wiki/Dapp-using-Meteor
EVM Simulator: https://github.com/EtherCasts/evm-sim/
Truffle deployment, testing, and asset creation environment: https://truffle.readthedocs.io/en/develop/
Dapple, a contract systems multi-tool: https://github.com/nexusdev/dapple
Populus, contract development framework written in python: https://github.com/pipermerriam/populus
Embark, dapp development framework written in JavaScript: https://github.com/iurimatias/embark-framework
Truffle Artifactor (formerly Ether Pudding) a package builder: https://github.com/trufflesuite/truffle-artifactor
Solium, a linter for Solidity: https://github.com/duaraghav8/Solium
Dapp design patterns: https://www.slideshare.net/mids106/dapp-design-patterns
Video about dapp design patterns: https://www.youtube.com/watch?v=XkJ8mg-R7C0&app=desktop
Nexus Dapp development blog: http://blog.nexusdev.us/
Dappsys: building blocks for dapps: https://github.com/dapphub/dappsys
Reddit Ethereum Developers board: https://www.reddit.com/r/ethdev/

