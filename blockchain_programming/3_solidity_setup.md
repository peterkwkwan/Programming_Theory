![Preface logo_grey.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/289b9105-b0c7-4556-9675-fcceff69a43b/Preface_logo_grey.png)

### **Setting up our smart contract**

Before we can code our smart contract, there is a three step process that we need to follow to set up our file properly.

**1) Providing a license for our open source code**

As we have learnt with the Web3 vision, a world where we use Web3 is a world where all source code is transparent and open source. The great thing about smart contracts deployed onto the Ethereum blockchain is that anyone can use a blockchain explorer and view these contracts. The smart contracts we will be building will be no different, as we are also going to be deploying onto the Ethereum blockchain.

The first step is therefore to add a license to allow for our code to be open source.

By using the main frame of the IDE, add this in the first line of your contract.sol file:

```solidity
// SPDX-License-Identifier: MIT
```

- The MIT license is one of the most common open source licenses. You can learn more about it here: [https://choosealicense.com/licenses/mit/](https://choosealicense.com/licenses/mit/)
- The two forward-slashes before the license is known as **commenting**, any text that goes after the two slashes is 'commented out' and will not be processed as code when the file is run.

**2) Stating the Solidity version**

The next step is to state what version of Solidity we are using. Since Solidity is a relatively new programming language, it does experience frequent updates. This is no different to other programming languages, such as Java or Python, who still have updates, albeit not as frequent as Solidity. Updating languages is normal, even in the real world! The English language has gone through many changes during its existence; new and old vocabulary, new and old sentence structures, it is always changing. Whereas change in human languages alter with time and natural adoption, programming languages alter through updates!

We can add an empty line after stating our license, then add another line to specify our Solidity version. There is no rule that forces us to add a specific number lines in between our code, as long as it is not in the same line.

We will then indicate what version our Solidity code is compatible with. This will give extra information to the compiler later on when compiling our Solidity into EVM Bytecode. It prevents incompatibility issues with older versions of the language.

As of the beginning of 2022, we are using version 0.8.0. Add the following line of code in:

```solidity
// SPDX-License-Identifier: MIT;

pragma solidity ^0.8.0;
```

- The **pragma** keyword tells Solidity which versions of the compiler are compatible with this file.
- We then state the language we are using, indicated by the word **solidity**.
- We add the compiler version afterwards. The caret symbol (^) can be added before the version to indicate that this file is compatible with all versions newer than 0.8.0.
- Since this is our first line of actual code (the license stated above is not code), we must add a semicolon (;) to the end the code. This will be a common rule throughout Solidity.
- All keywords are separated by a space.

**3) Creating the contract**

The final part of the set up is to create our contract. Add the following code in after stating the Solidity version:

```solidity
// SPDX-License-Identifier: MIT;

pragma solidity ^0.8.0;

contract MyFirstContract {

// The code of our contract goes in here!

}
```

- Add the keyword **contract** to indicate that this is the beginning of where the logic of our smart contract will be.
- Add the name of the smart contract afterwards. In the example, I have named it **MyFirstContract** just for simplicity's sake, you can name it anything as long as it does not have any spaces or punctuation within the name.
- Add two curly brackets ({ }) afterwards. Click in between the curly brackets and press enter / return. This will open up the brackets.
- We will be coding the smart contract logic in between these two curly brackets.