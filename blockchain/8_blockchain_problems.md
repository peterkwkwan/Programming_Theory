# Potential issues

### 51% attack

We learnt that malicious users can mine their own blocks and include invalid transactions in their block. By chance, they are able to find the correct nonce for the required hash and add their winning block to the blockchain, they won't be able to add their block unless they subsequently managed to create winning blocks repeatedly.
- Other nodes will just create a sub-chain and ignore their fabricated chain

However, if someone managed to control 51% of all mining power on the network, they could manipulate the history and future of the ledger. Thus, they would be able to create their own tampered chain

### Energy consumption

A lot of computational power is required to solve the mathematical puzzle