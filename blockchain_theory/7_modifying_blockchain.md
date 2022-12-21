# Modifying the blockchain

### Significance of chaining

How are blocks chained together? And how does it relate to security?

How does this prevent malicious activity on the blockchain?

### Overview

1) Data is inserted into the block
2) To ensure data is not tampered with, all data on the block is ran through a hashing function. This produces a *hash* for that block
3) The new block is 'chained' to the previous block by stamping the hash of the previous block onto itself
4) The first block of the blockchain does not have a previous hash (genesis block)

### Preventing malicious intent

Let's say a hacker wanted to manipulate some data on the block

However, due to the power of *hashing*, any data changes on the block will result in a completely different hash
- thus the block's hash will _change_
- the subsequent block will then realize the _previous hash_ that it stamped onto itself no longer matches the malicious block, and alerts the network
- this fake copy is then removed from the blockchain

This structure and process provides a key element of the blockchain
1) Security
2) Immutability
3) Transparency