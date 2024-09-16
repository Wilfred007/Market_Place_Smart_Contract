MarketPlace Smart Contract
Overview

The MarketPlace smart contract provides a decentralized marketplace where sellers can list items for sale and buyers can purchase these items. The contract manages items, tracks inventory, and processes transactions. It includes events to notify when items are added and purchased.
Contract Details

    Owner: The contract tracks the contract deployer as the owner.
    Items: Struct to store item details such as name, description, price, ID, and quantity.
    Seller: Struct to store seller information (name, shop address).
    Buyer: Struct for storing buyer name.

Functions
ListItems(string memory _itemName, string memory _itemDescription, uint256 _itemPrice, uint256 _id, uint256 _quantity)

    Description: Allows a seller to list items with their respective details.
    Parameters:
        _itemName: Name of the item.
        _itemDescription: Description of the item.
        _itemPrice: Price of the item.
        _id: Unique identifier for the item.
        _quantity: Available quantity of the item.
    Requirements:
        msg.sender must not be address(0).
        Item gets stored in the items mapping.

purchaseItem(uint256 _id, uint _quantity)

    Description: Allows buyers to purchase items.
    Parameters:
        _id: The unique identifier for the item.
        _quantity: The quantity of the item to purchase.
    Requirements:
        The item must exist (ID should not be 0).
        The buyer must send enough Ether to cover the total cost.
        The requested quantity must be available in stock.
        msg.sender must not be address(0).
    Updates:
        Updates the item quantity.
        Increases the contract balance.

getItems(uint _id)

    Description: Returns the quantity of an item by its unique identifier.
    Parameters:
        _id: Unique identifier for the item.

Events

    ItemsPublished: Triggered when an item is listed.
    ItemPurchased: Triggered when an item is purchased.

Requirements

    Solidity version: ^0.8.24.

Error Handling

    Address zero check: Ensures msg.sender is not the zero address for both listing and purchasing.
    Stock validation: Ensures buyers do not exceed available item stock.
    Sufficient payment validation: Ensures the buyer sends enough Ether for the purchase.

License

This smart contract is licensed under the MIT License# Market_Place_Smart_Contract
