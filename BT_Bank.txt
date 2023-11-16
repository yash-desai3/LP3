// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract bank
{
    mapping(address => uint) public user_Account;
    mapping(address => bool) public user_Exists;

    function createAcc() public payable returns(string memory)
    {
        require( user_Exists[msg.sender] == false , "Account already created!");
        user_Exists[msg.sender] = true;
        user_Account[msg.sender] = msg.value;
        return "Account is created";
    }

    function deposit(uint amount) public payable returns(string memory)
    {
        require( user_Exists[msg.sender] == true, "Account not created");
        require( amount > 0 , "Amount should be greater than 0");
        user_Account[msg.sender] += amount;
        return "ammount deposited";
    }

    function withdraw(uint amount) public payable returns(string memory)
    {
        require( user_Exists[msg.sender] == true, "Account not created");
        require( amount > 0 , "Amount should be greater than 0");
        require( user_Account[msg.sender] >= amount , "Amount is greater than money deposited");
        user_Account[msg.sender] -= amount;
        return "amount withdrawn";
    }

    function AccBalance() public view returns(uint)
    {
        return user_Account[msg.sender];
    }

    function AccExists() public view returns(bool)
    {
        return user_Exists[msg.sender]; 
    }
}
