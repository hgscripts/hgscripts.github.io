---
title: Developer guide
description: Developer guide for HG Auction System
icon: material/dev-to
---
# HG-Auction Developer guide

## Exports

### Toggle Auction Interface
Toggle the auction interface on and off
```lua
exports['hg-auction']:ToggleAuction()
```

### Force Close Auction Interface
If the auction interface is open, this forces it to close (Can be useful when a player is cuffed or dies etc...)
```lua
exports['hg-auction']:CloseAuction()
```

### Refresh Auction List
Refreshes the auction list for the player
```lua
exports['hg-auction']:RefreshAuction()
```

## Functions.lua

### Global notification settings

```lua
function AuctionGlobalNotification(auctionname--[[ (1)! ]], lastbetter--[[ (2)! ]], lastprice--[[ (3)! ]], identifier --[[ (4)! ]], img--[[ (5)! ]]) 
```

1. String
2. String
3. Float
4. String
5. Array<String\>


### New auction notification settings
```lua
function NewAuctionNotify(auctionname--[[ (1)! ]], price--[[ (2)! ]], isPrivate--[[ (3)! ]], img--[[ (4)! ]])
```

1. String
2. Float
3. boolean
4. Array<String\>

### Give item Function
Function to give the winner of an item his item
```lua
function giveitem(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. View [Give Reward Function](#give-reward-function)
2. View [Data Object](#data-object)

### Give Weapon Function
```lua
function giveweapon(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. View [Give Reward Function](#give-reward-function)
2. View [Data Object](#data-object)

### Give House Function
```lua
function givehouse(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. View [Give Reward Function](#give-reward-function)
2. View [Data Object](#data-object)

### Give Vehicle Function
```lua
function givevehicle(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. View [Give Reward Function](#give-reward-function)
2. View [Data Object](#data-object)

### Give Other Function
```lua
function giveother(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. View [Give Reward Function](#give-reward-function)
2. View [Data Object](#data-object)


### Give Reward Function
This is the function used to give out the rewards to the players and notify the winning player. Variable xPlayer is an object that represents the players (Dependant on the framerwork) 
```lua
function giveReward(xPlayer--[[ (1)!]], data--[[ (2)! ]])
```

1. Player object (Dependant on the framework used)
2. View [Data Object](#data-object)

### Check before adding an auction
This function is called before an auction gets added. You can add any logic you want. Return `false` to reject an auction.
```lua
function checkAvailability(data)--(1)!
```

1. View [Data Object](#data-object)

### Data Object
```lua
data = {
    id,--(1)!
    auctionname,--(2)!
    price,--(3)!
    category,--(4)!
    time,--(5)!
    endTime,--(6)!
    img,--(7)!
    plate,--(8)!
    itemname,--(9)!
    propertyID,--(10)!
    shellid,--(11)!
    lastbetowner,--(12)!
    lastbetidentifier,--(13)!
    lastprice,--(14)!
    isPrivate,--(15)!
    isBlackMoney--(16)!
    Itemcount--(17)!
}
```

1. Auction ID (int)
2. Auction name (String)
3. Starting price (float)
4. Category (string)
5. Starting time (int)
6. Ending time (int)
7. Auction pictures (Array<String\>)
8. Plate number for vehicles (string)
9. Item name (string)
10. Property ID for houses (int)
11. Shell ID for houses (int)
12. Last bidder's name (string)
13. Last bidder's identifier (string)
14. Last bid price (float)
15. Is auction private? (int, 0 or 1)
16. Is auction black money? (int, 0 or 1)
17. Item count (int)

### Admin permission check
This function is used to check whether the current player is an administrator or not. You can set this function to return false to disable the admin's add/edit/delete permissions.
```lua
function CheckIsAdmin(source, permissions--[[ (1)! ]])
```

1. Array<String\>