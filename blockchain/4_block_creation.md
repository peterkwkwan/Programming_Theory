# Block Creation

When a transaction is received by a node in the network, it will be *broadcasted* to all its other _peers_ in the network
- transactions are not automatically accepted by the nodes as each transaction must be _validated_

Validation happens based on 3 criteria:
1) If the amount outputted does not exceed the amount inputted
2) If the funds have not already been spent

The first 2 criteria are easy for the node to check. We only need to check that the sender's wallet has enough money as well as checking the history of transactions, to see if it was a duplicate transaction.

3) If the sender, who has chosen to send the funds, is actually the real sender!

The 3rd criteria is much more complicated. In the blockchain network, there is no KYC process and no intermediaries. How can we prove this? This is where *digital signatures* come into play.

### Digital Signatures - Symmetric encryption, single key

Encryption recap - allows us to encrypt some data (plain text) using a key, becoming cipher text, then using the same key to decipher the cipher text back into plain text.

> Since we are using the same key, this is known as _symmetric encryption_

The issue with using this method is that if we send the key over the internet, the key can get intercepted. Then the hacker would be able to read all our data without us knowing!

The solution would be to use *asymmetric encryption*.

### Non-digital signature - Asymmetric encryption

*Asymmetric encryption* uses multiple keys to transfer data.

Users create a *public key* and *private key*
- these always come in pairs and are _mathematically linked_ with each other
- usually in blockchain platforms, crypto wallets (like Metamask) will generate a pair of keys whenever a wallet is created

#### Public key

The public 'ID' of the user
- anyone on the blockchain is able to see this

#### Private key
Only the user can see this
- will never expose to this anyone and should keep it safe

