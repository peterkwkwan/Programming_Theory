# Block Creation

When a transaction is received by a node in the network, it will be *broadcasted* to all its other _peers_ in the network
- transactions are not automatically accepted by the nodes as each transaction must be _validated_

Validation happens based on 3 criteria:
1) If the amount outputted does not exceed the amount inputted
2) If the funds have not already been spent

The first 2 criteria are easy for the node to check. We only need to check that the sender's wallet has enough money as well as checking the history of transactions, to see if it was a duplicate transaction.

3) If the sender, who has chosen to send the funds, is actually the real sender!

