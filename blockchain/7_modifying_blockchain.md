# Modifying the blockchain

### Significance of chaining

How are blocks chained together? And how does it relate to security?

How does this prevent malicious activity on the blockchain?

### Overview

1) Data is inserted into the block
2) To ensure data is not tampered with, all data on the block is ran through a hashing function. This produces a hash for that block
3) The new block is 'chained' to the previous block by stamping the hash of the previous block onto itself
4) The first block of the blockchain does not have a previous hash (genesis block)