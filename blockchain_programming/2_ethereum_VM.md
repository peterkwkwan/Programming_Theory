# Ethereum Virtual Machine (EVM)

### How are smart contracts added to the Ethereum blockchain?

First, since we are deploying smart contracts to the Ethereum blockchain, we need to understand the Ethereum Virtual Machine.

![image](https://user-images.githubusercontent.com/37263010/209463378-3b98ec72-b99c-4a3d-8ea8-c7a808e395e0.png)

Higher level languages need to be compiled (translated) into binary code before fed into the computer for processing. Solidity is also a high-level language, and compilation also needs to take place, but with a few differences.

### What is the Ethereum Virtual Machine (EVM)?

__Virtual Machines__ are digital versions of physical computers, and can do almost everything a normal computer can do.

Why does Ethereum need its own virtual machine? That is because smart contracts are filled with complex code, therefore it needs an entire separate machine to process it.

Also, because it is decentralized, the computer must be virtual and cannot be owned by anyone. All Ethereum nodes can access the EVM. This is why Ethereum is also known as the "World's Computer", as any node can access this computer from anywhere.

### How does the EVM work?

1) Solidity code is written by a developer to create a smart contract.