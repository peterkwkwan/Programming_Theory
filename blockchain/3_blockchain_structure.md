# Blockchain structure

Combining what we learned about decentralization, distributed ledger technology and cryptography, we can now dive into blockchain

Blockchain exists virutally / digitally, it is not physical

- however, we can use a visual representation of _blocks_ to help us understand the blockchain concept

### Blocks

The blocks of the blockchain contain the _data_ of the _ledger_

The blocks are _chained_ together through _cryptography_

#### Blockchain network

If we only had _1_ copy of the blockchain, this would be a centralized ledger

- in order to achieve decentralization, we need more than 1
- this is why we refer to blockchains as having their own network (of ledgers)

A blockchain will have multiple participants, known as _nodes_

- nodes all have a copy of the ledger

A _blockchain network_ is therefore a network of distributed, decentralized nodes who all possess the same ledger of data

- the network needs a way to update all the ledgers with the latest copy, and how the nodes come to an agreement (consensus)

#### Peer-to-peer

The first practical use-case of blockchain technology was Bitcoin
- a way for us to send money without an intermediary

Let us consider this follow transaction

> Kevin sends $10 to Simon

> Simon sends $15 to Vivian

There are several questions we must pose in this case:

1. Who is checking that Kevin and Simon have enough money to perform such actions (who is validating these transactions?)
2. How does blockchain guarantee these transactions happen?
3. Is it possible to tamper with these transactions?

To answer all these questions, we must must understand the full process of a transaction taking place.
- these processes can be broken into 3 steps: