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

##### Public key

The public 'ID' of the user
- anyone on the blockchain is able to see this

##### Private key
Only the user can see this
- will never expose to this anyone and should keep it safe

#### Benefits of using two keys?

Allows us to:
- Encrypt some data using a private key (kept to yourself) and decrypt it using the public key (exposed to public)
- Encrypt some data using a public key (exposed to public) and decrypt it using the private key (kept to yourself)
- However, we are unable to encrypt & decrypt with just one key

Use case - Let's say you wanted to send a private message to a friend. Only your friend should be able to read it. Here are the steps:

1) You will type your message and *encrypt it using your friend's public key*, which is exposed to everyone
2) You will send the encrypted message to your friend
3) No one will be able to decrypt the message without the paired private key, which *only your friend possesses*
4) Your friend will receive the encrypted message and decrypt it using *their own private key*

A good analogy is a mailbox. Everyone knows your address, but only you have the key to open your mailbox.

However, if you lose your private key, everything in your wallet will be lost!

#### End-to-end encryption (e2ee)

Every message sent by the sender can only be read by the receiver. The middle man will only be able to see the encrypted data
- Services like Whatsapp and Facebook use e2ee

### Digital signature - Asymmetric encryption

The other use case os asymmetric encryption is known as *digital signatures*, a method used by blockchains to validate transactions.

To refresh our memory, transactions will only be valid if the network can check whether the sender of the transaction is actually the sender themselves. We prove this by creating a *digital signature*.

Here are the steps:
1) You have a transaction you want to initiate. This will be your own data
2) You will first *encrypt the data with your private key*. This is essentially creating a *digital signature* on your data. The data is now your private key encrypted data
3) You also have a copy of your data on hand, but not encrypted
- At this point, your have 2 things: a copy of your data that has been encrypted by your *private key*, and a copy of your *raw unencrypted data*
4) You send both of these copies to the blockchain network
5) The blockchain finds your public key, which is exposed to everyone, to decrypt the copy of your private key encrypted data
6) The blockchain will then compare the decrypted data and see if it matches with the raw unencrypted data you sent
7) If the data matches, then the network can be confident that the transaction is sent by you, as only you have ownership of your private key

#### Validating the transaction

To recap the validation process:

1) If the amount outputted does not exceed the amount inputted
2) If the funds have not already been spent
3) If the sender, who has chosen to send the funds, is actually the real sender!

All the nodes in the network run every single transaction through these 3 steps. If any steps fail, then the network will reject the transaction. 

If successful, the transaction is broadcasted to all nodes on the network to announce the validity of the transaction. It is then added into a block, ready to be *'mined'*.

What we get in end is a block full of transactions that have gone through validation checks. You can imagine us filling in a cardboard box (the block) with many books (the transactions), ready to be shipped off to the next stage of the blockchain process.