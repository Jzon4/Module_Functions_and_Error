# Module-Functions-and-Errors---ETH-AVAX

# VIDEO LINK

https://www.loom.com/share/b5966c54848b4f35bf3c9a69c8b84d8c?sid=d8bc61fc-2291-4777-99d3-a191893e4e39

# SUMMARY OF THIS CODE 
This Solidity smart contract is designed to manage orders for a pizza delivery service. Here's a summary:

Contract Name: MyNewContract
State Variables:
orderCount: A public unsigned integer to keep track of the total number of orders placed.
Order: A struct defining the structure of an order, containing the client's address, the pizza selection (represented by an unsigned integer), and a boolean indicating whether the order has been delivered.
orders: A mapping from order numbers (unsigned integers) to Order structs, allowing retrieval of order details by order number.
Functions:
placeOrder: A function for placing a new order. It takes a pizza selection as input and requires payment of at least 1 ether. Upon successful payment, it creates a new Order struct with the sender's address, pizza selection, and delivered status set to false. It increments orderCount and stores the new order in the orders mapping.
delivered: A function for marking an order as delivered. It takes the order number as input and sets the delivered status of the corresponding order to true. Additionally, it includes an assertion to ensure that the delivered status is indeed true after setting it.
Overall, this contract provides functionality for placing orders and marking them as delivered, ensuring payment is received before accepting an order, and maintaining order details on the blockchain. Additionally, it employs some best practices like using require for input validation and assert for internal consistency checks.

## MY CODE 

````javascript
// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

contract MyNewContract {
    
    uint public orderCount;

    struct Order {
        address client;
        uint donutSelection;
        bool delivered;
    }

    mapping(uint => Order) public orders;

    function placeOrderold(uint donutSelection) public payable returns(uint){
        if(msg.value >= 1 ether) {
            Order memory newOrder = Order(msg.sender, pizzaSelection, false);
            orderCount++;
            orders[orderCount] = newOrder;
        }
        else {
            revert("The required payment amount is not met.");
        }
        return orderCount;
    }

    function placeOrder(uint donutSelection) public payable returns(uint){
        require(msg.value >= 1 ether, "The required payment amount is not met.");
        Order memory newOrder = Order(msg.sender, donutSelection, false);
        orderCount++;
        orders[orderCount] = newOrder;
        return orderCount;
    }

    function delivered(uint orderNumber) public {
        orders[orderNumber].delivered = true;
        assert(orders[orderNumber].delivered == true);
    } 
}
````

## Author

Jayson C. Alejandro BSIT
@Jzon4

# LICENCE
Copyright (c) 2024 Jzon4
