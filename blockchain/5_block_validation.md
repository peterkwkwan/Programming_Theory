# Maintaining the blockchain

Once the transactions are verified and the blocks are filled, they are ready to be officially added to the blockchain.

There are, however, thousands of transactions being initiated around the world every second. We can assume that different nodes will have a different order of transactions inside their respective blocks. 

Once all these blocks are filled with transactions, it begs the question - which block gets the right to be chosen and added to the blockchain first?

> The choosing process is called the _consensus mechanism_. It indicates _how_ the blockchain network comes to a consensus regarding which block gets added to the blockchain.

### Finding the lucky number

The following process takes place to select the next block:
1) the blockchain network releases a mathematical puzzle to all nodes on the network. Each node is aiming to add their block onto the blockchain
2) the mathematical puzzle involves finding a specific number that when added with the transaction data included into the block and hashed, will output a 'target hash' that is accepted by the network
3) This specific number is known as the *nonce*, which is just an arbitrary number used just once in a given cryptographic communication. The nonce is the answer that all the nodes are trying to find
4) the target hash is a random hashed text, and it is incredibly difficult to find the solution

### Race for the nonce

Finding the correct nonce is a matter of trial and error
- nodes must go through a strenuous process of guessing the correct number that will give them the right to add their block to the blockchain

> The block that gets chosen to be added is decided by which node manages the find the nonce *first*. 

Once a node manages to find the correct hash, the new block is added onto the blockchain and broadcasted to all the other nodes, who then give up the race and await the next mathematical puzzle to be released

The cycle repeats when the next puzzle is announced

This entire process of validating the transactions, racing to find the nonce, and adding the block onto the blockchain is known as *mining*.

### Why this difficult?

Mining is essentially a brute force way to the correct nonce. This requires a lot of energy!

The reason for this difficulty is because of security. This entire process makes is harder for fake transactions to get added to the network. Instead, the blockchain requires the participants to go through the hard work, hence the name *Proof-of-Work*


### Miners