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
            Order memory newOrder = Order(msg.sender, donutSelection, false);
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
