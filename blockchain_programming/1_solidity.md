# Solidity

### What is Solidity?

- high-level language used to create smart contracts
- main purpose is to create smart contracts to be deployed onto the Ethereum blockchain

### Smart Contracts

- simple a program that runs on the blockchain
- a collection of code that resides at a specific address on the blockchain, and automatically runs when predetermined conditions are met

Are essentially mini-programs implanted into the network, waiting to be activated
- e.g. virtual vending machines
    1. We select our item of choice.
    2. We pay the vending machine.
    3. The vending machine returns us with the item of our choice.
    - 
- The vending machine is automatically programmed to carry out a set of instructions based on some inputs (your choice and your money) and returns some outputs (the item).
- Anyone can program these smart contracts, or 'vending machines', and send them to the blockchain. They will exist on the blockchain forever and wait for some inputs of data and return users with the programmed outputs, automatically and without fail.
- The capabilities of smart contracts can be extremely flexible. Anyone is now able to build simple or complex applications on the blockchain, with the applications now having the additional powers of blockchain trust and security.

### DApp (Decentralized application) Architecture
- DApps are just applications that run on decentralized network
- Backend operations of a DApp are written into smart contracts, then uploaded to the blockchain and live there forever
- Smart contracts wait for their preconditions to be met, then if activated, execute the operations autonomously

#### Scenario: NFT Marketplace transaction (Buyer to seller)

1) Buyer accesses NFT site from web browser
2) Browser connects to frontend of the NFT site
3) Buyer connects their digital wallet to the website by providing their digital signature
4) Buyer clicks 'BUY'
5) Frontend sends the data to a '__provider__' that allows users to access the blockchain nodes. Buyer provides the _provider_ the cryptocurrency for the purchase
6) The _provider_ searches for the smart contract