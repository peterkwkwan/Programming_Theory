# The Longest Chain

### Block Validation Recap
All nodes on the blockchain network carry a copy of the blockchain. Nodes who participate in the mining process race towards producing the correct hash to add their new block of transactions onto the chain. When they win this race, the winning block is broadcasted towards the network, where _all other nodes stop what they are doing, check that the winning block is valid and add it onto their copy of the blockchain_.

### Look for the longest chain

Once the winning block is determined, the block is _not immediately added to the blockchain_
- *all other nodes on the network will check to see if the new block being added is legitimate*

There is a _slim_ chance that two blocks find the correct nonce that outputs the correct hash and are mined *at the same time* as each other
- some nodes will accept 1 and not the other!
- what results is a blockchain split in two, known as a *fork*

If a fork results, the *longest chain rule* applies
- subsequent new winning blocks will choose the longest chain to add onto
- the other _sub-chain_ will be discarded