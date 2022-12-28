## Deploying our smart contract

At this point, you might be thinking - we can already deploy our contract?

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract MyFirstContract {

}
```

Indeed, we can! What we have just created might have seemed too short and easy, but we have actually coded an empty smart contract. Even though the contract is empty, it is still deployable.

**1) Compiling from Solidity to EVM Bytecode**

The SOLIDITY COMPILER should pop up in the side panel. It may look quite complicated, but we can ignore more of the buttons for now.

- All we need to pay attention to is the **COMPILER** version, which according to the screenshot, is using version 0.8.7. Remember we stated in our file that our file accepts any Solidity version newer than 0.8.0.
- We can then click on the big blue 'Compile contract.sol' button. If there are no errors in code, our contract will be converted from Solidity to EVM Bytecode.
- You can also use the shortcut CMND + S (Mac) / CTRL + S (Windows) to compile your contract without having to click on the button every time.
- A green tick should appear next to the Solidity icon inside the icon panel. That means your file has been successfully compiled.


**2) Deploying our contract**

Next, click on the icon that looks like the Ethereum logo with an arrow pointing rightwards. This will bring up the DEPLOY & RUN TRANSACTIONS in the side panel. There are a few important things to note here.

- The **ENVIRONMENT** option is indicating where you will be deploying your smart contract to. The default setting is the 'JavaScript VM', which is a test blockchain that exists within the browser. This is extremely useful as we can test our smart contracts without having to actually interact with the actual blockchain, which would otherwise be expensive and timely.
- You can also see that it provides us with other options such as **Injected Provider**, which allows us to connect with a provider such as Metamask, or **Web3 Provider**, which allows us to connect with our own locally hosted node.
- The **ACCOUNT** option lists the wallets that we are connected to and can use to deploy our smart contract. Remember, deploying smart contracts and interacting with the blockchain has transaction fees (gas), which is why we need to also provide Ether.
- Right now, you can see that we have multiple accounts all with 100 ether. This is because we are connected to the fake JavaScript blockchain, and it has provided us accounts for testing. If we were connected to our Metamask wallet (in our ENVIRONMENT option), we would be able to see our actual wallet balances in our Metamask.


Click on the 'Deploy' orange button. There a few things we should pay attention to.

- In your terminal, on the bottom right of the screen, a green tick should appear. That indicates that the contract has been successfully deployed (in this case, onto the fake browser blockchain).
- In the side panel, scroll down and you will be able to see that there is a blue (1) icon next to **Transactions**. That is providing indication that one transaction has been made onto the blockchain, which is the deployment of the contract.
- You will also be able to click on a drop down arrow underneath **Deployed Contracts**. This area of the Remix IDE is extremely important as it allows us to interact with our contract, to see whether it's working. Since the contract we have made doesn't actually have anything inside, there is nothing to interact with. We will revisit this in the future when we make more complex smart contracts.


- Another very important observation is also looking at our account balance. If you recall, we started off with 100 ether, but now we have a bit less than that. Deploying the smart contract has costed us gas fees in the form of Ether. All transactions on the blockchain cost something!


Congratulations! You've deployed your first smart contract with Solidity!