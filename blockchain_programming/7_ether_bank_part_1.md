![Preface logo_grey.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/289b9105-b0c7-4556-9675-fcceff69a43b/Preface_logo_grey.png)

### EtherWallet Project

It’s time for our next project, where we focus more on cryptocurrency (specifically Ether) transactions within smart contracts.

In this smart contract, we will attempt for the contract to have the following functionatlities:

- A variable that stores the amount of ether received
- A function that allows a user to send money to the contract
- A function that returns us with the balance of the current amount of Ether
- A function that allows us to withdraw the money from the contract to our wallet
- A function that allows us to withdraw the money from the contract to a specific wallet

**1) Setting our contract up**

As per usual, we will need to follow our same steps to set up our contract:

- Specify the open-source license
- State the version of Solidity we are using
- Add the contract keyword as well as the name of the smart contract

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {

}
```

**2) Creating our ether received variable**

We will be monitoring the amount of Ether that the contract has received at different points of time, which is why the first thing we’ll create is a variable that indicates the total amount of et received by the smart contract.

Add the following code below:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
}
```

Since our ether balance will be some numerical value, we will give it the data type of an unsigned integer. 

We will also make it a publicly viewable variable. 

We will provide the variable a straightforward and simple name - etherReceived.

**3) Function to send money**

Let’s begin to create a function that allows us to enter a specific amount of ether and send it to the smart contract.

A preview of the code to be added:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
	
	function sendMoney() public payable {
		etherReceived = etherReceived + msg.value;
  }
}
```

There will be a few new concepts that we will be coming across in the creation of this function.

As per standard practice, we will define our function using the **function** keyword, followed by the name of the function.

The function will also be a public function so anyone can interact with it.

### **Payable**

Previously we learnt about **view** functions. View functions do not change the state of the blockchain as the function simply reads the state of the blockchain and does not charge the user with gas. This was known as a function modifier, a type of function.

Another type of function that we will be using is a **payable** function, which simply means that the function can send and receive Ether. If Ether is sent to a function that does not state a payable modifier, then the transaction will be rejected.

We can add the payable keyword after the visibility modifier (public).

```solidity
function sendMoney() public payable
```

### Global Variables

Next, we will need to provide logic to our sendMoney function so that our smart contract is able to receive the sent Ether.

All we will need to do is let a user send Ether to the contract, then add that amount of Ether to our etherReceived variable.

But how do we retrieve the Ether amount from the user of the smart contract? This is where we can use a global variable.

Global variables are variables that already exist inside the smart contract without us having to define them.

For example, the **msg** global variable allows us to access data from the person utilising the smart contract.

- **msg.sender** refers to the address of the current user interacting with the smart contract
- **msg.value** refers the amount of money that is being sent in the current transaction
- **this** refers to the current smart contract

In the case of our sendMoney function, we need to retrieve the amount of Ether being sent in the current transaction and add it to our variable. Thus, the code becomes:

```solidity
function sendMoney() public payable {
	etherReceived = etherReceived + msg.value
}
```

**Testing via contract deployment**

Compile and deploy the contract. You should now see one button that indicates the etherReceived variable and also a button for our sendMoney function.

In ‘Deploy & Run Transactions’, you should be able to see an input box that allows you to indicate the amount of Ether to be included in your transaction.

![Screenshot 2022-05-27 at 12.33.52 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/88741b0a-96d8-4154-9f3d-dc5e7efd8091/Screenshot_2022-05-27_at_12.33.52_AM.png)

![Screenshot 2022-05-27 at 12.35.54 AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/299e2903-4abc-43e6-87c9-61e7827296a8/Screenshot_2022-05-27_at_12.35.54_AM.png)

Try and set the Ether amount to be 1, then click on the **sendMoney** button down below.

There should be two things to notice:

1. If you click on the **etherReceived** variable, you can see that there is now 1 ether stored inside the variable.
2. If you look at your wallet amount, there should be some ether deducted from the original amount (previously 100 ether).

**4) Function to check balance of current smart contract**

As of right now, our variable etherReceived only tracks the total amount of ether that the contract has received. If we want to check the current balance of the contract, we will need to create a function for this.

A preview of the code to be added:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
	
	function sendMoney() public payable {
		etherReceived = etherReceived + msg.value;
  }

	function getBalance() public view returns(uint) {
		return address(this).balance;
	}
}
```

Let’s begin by naming our function.

```solidity
function getBalance()
```

Next, we will state the visibility and function modifiers needed to retrieve the current balance. We will make the function a public function and specifically a **view** function, since we are not changing the state of the blockchain but simply want to read from it. 

```solidity
function getBalance() public view 
```

Since we want the function to actually return us with a figure, we will add in a **return** keyword and expect an unsigned integer to be returned to us.

```solidity
function getBalance() public view returns(uint) {
}
```

The final step is to add the logic of our function. The question is - how do we access the amount of ether that is stored in the contract. This is where we can use another previously mentioned global variable - **this**. 

```solidity
function getBalance() public view returns(uint) {
	return address(this).balance;
}
```

The ‘this’ keyword refers to the current contract. We can therefore use the .balance property to access the current balance of the current contract’s address.

**5) Function to withdraw ether from smart contract**

Our contract won’t be all that useful if we can only send ether to it, but not be able to take the ether back out. That’s why we’ll be making one last function to withdraw the ether from our contract.

Preview of our code to be added:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
	
	function sendMoney() public payable {
		etherReceived = etherReceived + msg.value;
  }

	function getBalance() public view returns(uint) {
		return address(this).balance;
	}

	function withdrawMoney() public {
		address payable to = payable(msg.sender);
		to.transfer(getBalance());
	}
}
```

We will begin by stating our function’s name, as well as its visibility modifier. Since this function will change the state of the blockchain, it is not a view function. It will actually initiate a transaction.

```solidity
function withdrawMoney() public {
}
```

Next, we need to specify where the ether is being withdrawn. We can create an address variable named **to** (or anything you prefer), which will refer to the address of the user that is interacting with the contract. We also need to state that the variable and address is payable.

```solidity
function withdrawMoney() public {
	address payable to = payable(msg.sender);
}
```

Now that we have an address to send the ether to, we will use the .transfer() method (can be used on any address) and send the ether of the contract to the stated address. We can get the amount of ether by retrieving the current balance of the contract through our previously created getBalance() function.

```solidity
function withdrawMoney() public {
	address payable to = payable(msg.sender);
	to.transfer(getBalance());
}
```

**6) Function to withdraw ether from smart contract to specific address**

To provide our function additional functionality, we will also create a function that allows us to specify the address of which we want to send our ether to.

Preview of our code to be added:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
	
	function sendMoney() public payable {
		etherReceived = etherReceived + msg.value;
  }

	function getBalance() public view returns(uint) {
		return address(this).balance;
	}

	function withdrawMoney() public {
		address payable to = payable(msg.sender);
		to.transfer(getBalance());
	}

	function withdrawMoneyTo(address payable _to) public {
		_to.transfer(getBalance());
	}
}
```

Start by giving a name to the function.

```solidity
function withdrawMoneyTo
```

Unlike the functions that we created, this time our function will need a parameter which allow us to indicate the address of which we want to send the ether to. The parameter will accept an address value, which must also be payable to accept the ether.

We will provide the parameter the name of **_to**.

```solidity
function withdrawMoneyTo(address payable _to)
```

Let’s also make the function a publicly usable function by providing the public visibility modifier.

```solidity
function withdrawMoneyTo(address payable _to) public {
}
```

Finally, the logic should be the same as our other withdrawMoney() function. We will also retrieve the amount stored in the function through the getBalance() function.

```solidity
function withdrawMoneyTo(address payable _to) public {
	_to.transfer(getBalance());
}
```

**5) Compile, Deploy & Test**

Congratulations! You’ve created a simple smart contract that allows us to send and store ether, as well as withdraw ether out of the contract.

Test it out by sending ether, checking the balance, withdrawing the ether, then checking the balance again!

Final code:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract EtherBank {
	uint public etherReceived;
	
	function sendMoney() public payable {
		etherReceived = etherReceived + msg.value;
  }

	function getBalance() public view returns(uint) {
		return address(this).balance;
	}

	function withdrawMoney() public {
		address payable to = payable(msg.sender);
		to.transfer(getBalance());
	}

	function withdrawMoneyTo(address payable _to) public {
		_to.transfer(getBalance());
	}
}
```