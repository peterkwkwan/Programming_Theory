# Cryptography

### Encryption
Is a technique used to storage of data through *encryption* ('scrambling' of information)
- ensures that only the sender and intended recipient of a message can view its contents
- "The Imitation Game" - cracking the German's Enigma machine

### Hashing
The process of transforming some set of data into random values that _can't be reversed_ is called *hashing*
- Many sites use this technique to store user passwords

### Encryption vs Hashing
- Encryption is a _two-way process_ of using a key to convert data into encrypted information
    - commonly known as cipher text
    - use the same key to convert the encrypted information back to its original form

- Hashing is a _one-way process_, meaning we cannot retrieve the data in its original form
    - once hashing has happened it cannot be reversed

If passwords were encrypted instead of hashed, the hackers would be able to reverse-engineer and decrypt the passwords

### SHA256 algorithm

The most well known algorithm used in blockchain is known as _SHA256_
- designed by the United States National Security Agency

The most interesting aspect of hashing is that the output has a fixed length - and every unique input gives a different output