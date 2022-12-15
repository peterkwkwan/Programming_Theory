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

### Suspicion on the blockchain

Let's say a hacker wanted to put their own false transaction on the blockchain
- if they find the correct nonce and appropriate hash, they will be able to add their block to the chain. They will try to broadcast it out to the network

When the other nodes do their validation check on the block, they will notice there is a false transaction inside the winning block, and being their suspicions
- When the next winning block is created, it will try to find another sub-chain to add their block to, or create their own sub-chain
- So unless the hacker manages to repeatedly find the correct nonce and required hash (extremely unlikely!), forcing the creation of its own longest chain, all suspicious activity will be discarded as the other nodes will choose not to add onto the suspicious sub-chain