### Functions

It's time to move onto the next fundamental in Solidity programming - functions! So far, our SimpleStorage smart contract has one variable named myUint, that we can manually assign an integer to. Let's try to add further functionalities into our contract.

We will try to do the following:

- Create a way for us to change the value stored in our myUint variable.
- Create a way to retrieve the value stored in our myUint variable.

As you can imagine, these functionalities require a bit more than just variables. This is where we need to use functions.

**Functions are blocks of code that help us to achieve a specific outcome**. They are programs that wait for some data, process that data based on its programmed instructions, and provide an output. Think of an oven as a function, we insert some food to the oven, it cooks the food based on the heat we set it as, and it returns us with the baked food. Just like an oven, functions serve specific purposes, based on what we instruct it to do.

Functions are more complex than variables and require more syntax to create one. We can usually split up a function into three parts:

1. Function name
2. Function type
3. Return types
4. Function logic

![image](https://user-images.githubusercontent.com/37263010/210136835-47c71e78-fa52-45ac-add9-00785fe3ce8c.png)

### Function #1 - changeValue

Let's add our first function into our smart contract. This function will change the stored value of our myUint.

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public myUint = 10;
    
    // add new code below!
    function changeValue(uint256 _newUint) public { 
        myUint = _newUint;
    }
}
```

We’ve added the following code below:

```solidity
function changeValue(uint256 _newUint) public { 
    myUint = _newUint;
}
```

Let's dissect each part of the function we've added.

**1) Function name**

We start off creating our functions by adding the keyword 'function'.

```solidity
function
```

We then add our function's name. In this case we've named our function **changeValue**, as we want this function to change the existing stored value. Naming our functions are similar to naming variables, as long we don't have spaces within the name, the function is good to go.

Our function's name is followed by two rounded brackets. Inside our brackets, we will state our **parameters**. A parameter is simply just some information the function will take in for processing.

In the case of our oven, the parameter is the food that is taken into the oven. In the case of the function we are trying to create, the parameter will be the new value that we will assign our variable. We have named our parameter **_newUint** (we can name our parameter whatever we wish!). We also need to state what type of data the value taken in will be. In this case, we have stated that it must be a uint256.

```solidity
function changeValue(uint256 _newUint)
```

**2) Function type**

We then need to state a few details on the type of our function.

The first is stating stating the function's visibility. Visibility works the same way as variables. As previously mentioned, going into the different visibilities is beyond the scope of this lesson, so we will assign this function the **public** visibility.

```solidity
function changeValue(uint256 _newUint) public
```

**3) Return type**

Since the purpose of our function is to update an existing variable, we will not need any value returned to us. Therefore, we do not need to add the returns keyword. More on this later!

**4) Function logic**

Finally, we can add our curly brackets afterwards and add our logic within the brackets. This is where the logic of our function comes in.

```solidity
function changeValue(uint256 _newUint) {
// logic goes here!
}
```

The final line of our code will instruct the function to update the value inside our variable.

```solidity
function changeValue(uint256 _newUint) {
	myUint = _newUint;
}
```

**Deploying contract**

Great! We have created our first function called changeValue. Let's try to deploy the smart contract now. Follow the same steps to deploy your contract:

- CTRL / CMND + S to compile your Solidity file to EVM bytecode.
- Click on the 'Deploy' button.

We should now have a new way to interact with our contract. As you can see, there is now an orange button and an input that represents the changeValue function that we previously created.

![image](https://user-images.githubusercontent.com/37263010/210136861-96419b2d-3ab0-4deb-a522-8d099a225fe4.png)

Just as we have coded, the changeValue will take in a piece of information, in this case the parameter **_newUint** must be a uint256.

Try to add in an integer of your choice into the input box. Afterwards, click on the orange button that displays the function's name, changeValue. There are a few things to note:

- In your terminal, you will see a green tick, indicating that a transaction has gone through. We have sent a transaction to the blockchain to indicate that the value stored in the variable has changed.

![image](https://user-images.githubusercontent.com/37263010/210136915-e629fdbe-903a-4f75-bfe6-ea77e1cbe177.png)

- Also take a look at the amount of ether in your wallet. It has decreased! Recall that changing any data or state on the blockchain requires a transaction fee.

![image](https://user-images.githubusercontent.com/37263010/210136932-be0acdac-6d18-418f-be01-fd59c8257581.png)

- Click on the myUint public variable in your contract. It should now store the value that you set using the changeValue function.

### Function #2 - retrieveValue

Let's now try to add another function into our contract. This time, the function will retrieve the value stored inside the myUint variable.

Add the new code below:

```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public myUint = 10;
    
    function changeValue(uint256 _newUint) public { 
        myUint = _newUint;
    }

    // add new code below!
    function retrieveValue() public view returns (uint256) {
        return myUint;
    }
}
```

We've added the following code below:

```solidity
function retrieveValue() public view returns (uint256) {
    return myUint;
}
```

Let's dissect each part of the function.

**1) Function name**

Since our function is going to retrieve the value of the variable, we will simply call our function **retrieveValue**.

This time, our function will not require any parameters, since the sole purpose of the function is to retrieve the value, not to update it. As such, no extra information will be passed into the function when we use it.

```solidity
function retrieveValue()
```

**2) Function type**

Again, our function is going to have a **public** keyword so that it is accessible by anyone.

```solidity
function retrieveValue() public
```

However, before we move onto step 3 with return types, we need to add another keyword after our visibility modifier that will further specify what kind of function this is.

Because our function is only going to retrieve data from the blockchain and not alter it, this function will be a read-only function. The official name for these functions are called **view functions**. They are only used to view the data on the blockchain.

Since the state of the blockchain is not being changed, the usage of this function will not require any gas fees.

```solidity
function retrieveValue() public view
```

If you recall for our previous **changeValue** function, we did not need to state any function type. The reason is because functions by default are intended to change the state of the blockchain. If there is no 'view' keyword after the visibility modifier, we can assume that it is a default state-modifying function.

**3) Return type**

In our previous function, we simply used it to update the myUint variable. We did not need any value returned to us when using the function. However, with our retrieveValue function, we will need a value returned to us, since we are trying to retrieve some data.

That is why we will have to add in a **returns** keyword.

```solidity
function retrieveValue() public view returns
```

We also need to specify the type of data the function should return. If our myUint variable will only ever be a uint256, we should also make sure that the value being retrieved is also a uint256. We add this additional information in right after the returns keyword, with a pair of rounded brackets.

```solidity
function retrieveValue() public view returns (uint256)
```

**4) Function logic**

Great! We have successfully declared our function along with the necessary details. We will add the curly brackets as with all functions and proceed to add the logic to our function.

```solidity
function retrieveValue() public view returns (uint256) {
	// logic goes here!
}
```

The logic for this function is simple. Again, we are only retrieving the value stored in our variable. Furthermore, because we stated that our function would return a value, we will need to specify exactly what it will be returned.

We can thus add the **return** keyword within the logic of our function, and return the myUint variable. The logic describes that this function will return whatever the current value of myUint is.

```solidity
function retrieveValue() public view returns (uint256) {
	return myUint;
}
```

Any time we specify a **returns** keyword inside the declaration of a function, we must also use the **return** keyword somewhere inside the logic of our function to specify exactly what is being returned.

Congratulations! Our second function is now complete. It is time to deploy our updated smart contract.

**Deploying contract**

Let's follow the same steps to deploy our smart contract.

- CTRL / CMND + S to compile your Solidity file to EVM bytecode.
- Click on the 'Deploy' button.

Our smart contract now has three ways to interact with it!

Try and use the changeValue function to change the myUint value. Then click on the retrieveValue function to retrieve the updated value.

You can also note that when using the retrieveValue function, no ether is being consumed as it is a read-only view function.

**The difference between myUint & retrieveValue**

One final thought you might have is what the difference between retrieveValue and myUint is, and why they essentially act the same.

The fact is, they do act exactly the same. When we create public variables, what happens is that Solidity automatically gives them the logic seen within our retrieveValue function. It gives these public variables a read-only view functionality.

However, you can also imagine that there is so much more to learn in Solidity, and that functions can be much more complex and perform all sorts of complicated tasks. This lesson was just to demonstrate the power of functions in an introductory level.
