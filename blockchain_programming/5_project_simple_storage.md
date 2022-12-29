### SimpleStorage

Now that we've become more familiar with the Remix IDE, understand what a smart contract in Solidity looks like and how to compile and deploy one, it's time to move onto our first proper Solidity project.

The SimpleStorage project is a famous project that is often used as an introduction to Solidity. Our objective is to create a smart contract that allows us to:

- Initially store some data
- Be able to retrieve that data
- Have the option to update the stored data

Three simple data storage functionalities of our smart contract, hence the name 'SimpleStorage'. Although this may seem like a very simple project, it does a great job describing what smart contracts are used for on the blockchain - the storage and manipulation of data in a transparent and immutable way.

**Start off by creating a new file in your Remix IDE.**

![image](https://user-images.githubusercontent.com/37263010/209898660-e82b77ed-0ff9-4ac7-b305-0f2114adaf4a.png)

Click the new file button in your side panel. Call your new Solidity file 'SimpleStorage.sol'.

Add the following code in your smart contract:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {

}
```

The setup is the same - we need an open-source license identifier, a line of code to state our Solidity compiler compatibility and also a line of code to initiate our smart contract along with our contract's name. We will name our new smart contract 'SimpleStorage'.

### Variables

One way to look at programming is that we are trying to manipulate data. If we manipulate the data correctly and provide it in a computer-friendly format, the computer will accept it as a list of instructions and carry out the requests.

In any program, managing data can get very messy. We can use **variables** to help us with this. Variables are simply containers of data. They allow us to store and retrieve data whenever we need to.

If we want to create a variable in Solidity, there are three details of the variable that we must specify: data type, access modifier and variable name. We will explore each of them one at a time.

Let's start off by creating a variable in our smart contract. Add the following code:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public myUint; // Add this line!
}
```

### Data Types

Unfortunately, variables in Solidity are not one-size-fits-all data containers. This is why the first detail of the variable that needs specifying is what type of data our variable accepts. In programming, each language has their own data types that they use. We will explore the different types that exist in Solidity.

**Boolean**

The boolean data type is used to store boolean values, which can only either be **true** or **false**.

```solidity
bool // e.g. true or false
```

**Integers**

The integer data type is used to store integer (whole number) values.

- There are two types of integers: int (integer) and uint (unsigned integer). The only difference between them is that the uint data type only includes positive numbers, whilst the standard integer contains both positive and negative numbers.
- The integer data type can also have a 'bit' value after the data type. This just indicates the range of numbers it can hold, 256 bit integers can hold a lot more data than their 8 bit counterparts. For now, we can concentrate on using the 256 bit versions of int and uints.
- The reason why Solidity cares about such intricacies is because any extra data needed to be saved onto the blockchain will mean more gas fees! You will slowly start to see this common theme of 'less data, less gas' during our Solidity programming.

```solidity
int256 // e.g. 20 or -20
uint256 // e.g. 20
```

**Address**

The address data type holds a 20-byte value, which represents an Ethereum address. This data type is extremely important in accessing an account's balance or transferring fees to an account.

```solidity
address // e.g. 0xc0ffee254729296a45a3885639AC7E10F9d54979
```

### Visibility Modifiers

In Solidity, we are constantly dealing with users of the blockchain interacting with the smart contracts that live within. When programming these contracts, security of the contract is of utmost importance.

At certain times, we may want to specify who can access the data written into these contracts. Can the data only be accessed if a user is directly interacting with the contract? Or can the data of this contract be accessed by other external contracts? Or by anyone without any restrictions? Specifying who can or cannot access the data describes the **visibility** of some given data.

This is why when creating any variables (or functions, as we will learn later on), we need to specify what is known as a **visibility modifier**. These visibility modifiers allow us to specify who can control/access what inside our smart contract. They are placed right after we specify the data type of the variable.

There are four visibility keywords we can use: **public**, **private**, **internal** and **external**. Going through each of these keywords is beyond the scope of this lesson, so we will only focus on the public visibility modifier.

**Public** - The public visibility keyword allows our variable to be accessed within our current smart contract and also in other external smart contracts.

```solidity
public
private
internal
external
```

### Variable Names

The last part of our code is simply the name of the variable. Recall that variables are just containers of data. In this case our variable is called **myUint,** 
stores a uint (unsigned integer) and has public visibility.

- Variable can be named anything, as long as there are no spaces within the name.

### Assigning values to variables

You may have realised that within the process of creating our first variable, we never actually gave it a value. We've created a container but haven't put anything inside it.

We can use the equals (=) sign to assign values to variables. Let's try to give our myUint variable the value of 10. Your line of code should now look like this:

```solidity
uint256 public myUint = 10;
```

We have now successfully created a variable called **myUint**, which holds the data type of **uint256**, has public visibility and holds the integer of **10**.

The interesting thing is that had we run our code before assigning it the integer of 10, our contract would have still worked. The reason why is that **all variables have a default value depending on their data type**. If we did not assign the value of 10, our myUint variable would automatically hold the value of 0.

Each data type has their own default value.

```solidity
// Default values
uint256 myUint = 0;
int256 myInt = 0;
bool myBool = false;
address myAddress = 0x0000000000000000000000000000000000000000;1
```

### Deploying Contract

Now that we have created a variable, let's try to deploy our smart contract and see what we can do with it.

Follow the same steps as before to deploy your contract.

Compile your contract, either by clicking on the Solidity compiler in the icon panel and clicking on 'Compile SimpleStorage.sol' or using the CMND / CTRL + S shortcut.

Deploy your contract by clicking on the Deploy & Run Transactions in the icon panel and clicking on 'Deploy'.

Scroll down the Side Panel after clicking Deploy, and view the 'Deployed Contracts' by clicking on the drop down.

You should see that we now have a button to interact with in our smart contract. Clicking this button allows us to retrieve the data that is stored in our variable that we programmed, myUint.

Smart Contract:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public myUint = 10;
}
```

Output:


- Note that we can also try and deploy the contract without assigning a value to our variable, to see the default value that becomes assigned.

Smart Contract:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public myUint;
}
```

Output:


- We should also remember that every time we deploy our contract, a small portion of our Ether gets consumed as gas fees!
