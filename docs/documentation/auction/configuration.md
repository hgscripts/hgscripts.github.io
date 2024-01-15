---
title: Configuration
description: Configuration documentation for HG Auction System
icon: fontawesome/solid/gear
---
# HG-Auction Configuration Documentation

## Config.lua
### General Settings
```lua
Config.Framework = "newesx" --(1)!
Config.Theme = "default" --(2)!
Config.OpenCommand = "auc" -- (Command or `#!lua false` to disable it)
Config.Categories = { --(3)!
    "all",
    "car",
    "home",
    "item",
    "weapon",
    "other"
} 
Config.discordlog = "" --(4)!
```

1. Framework to use: "newesx", "oldesx", "newqb", or "oldqb"
2. Change the color theme of the interface. Set the name to the `data-theme` attribute in your `theme.css` file. [Read more here](#customization)
3.  Available Categories

    |               |
    | --------      |
    | **all**       |
    | **car**       |
    | **home**      |
    | **item**      |
    | **weapon**    |
    | **other**     |


4. Discord webhook URL
!!!note
    You can only remove categories. You cannot add more.
### Language Settings
Change the language to any of the provided locales
```lua
Config.Lang = "en"
```
You can add a language or modify an existing one very easily. Simply navigate to the `web/assets/locale` directory:
```
.
└── hg-auction/
    └── web/
        └── assets/
            └── locale/
                ├── en.json
                └── *.json
```
There, you'll find json files that have the translations for the panel. You can modify the existing ones. To add another language, simply copy one of the existing files (ex: `en.json`) and rename it to something else (ex: `fr.json` for French) And change the text.

Example:
<div class="grid" markdown>

```json title="en.json"
{
    "BALANCE":"Balance",
    "CATEGORY_ALL":"All",
    "CATEGORY_VEHICLES":"Vehicles",
    // Rest of the file
}
```

```json title="fr.json"
{
    "BALANCE": "Solde",
    "CATEGORY_ALL": "Tous",
    "CATEGORY_VEHICLES": "Véhicules",
    // Rest of the file
}
```

</div>

Next, simply change the value to whatever you named the file 
```lua
Config.Lang = "fr"
```

### SQL Settings
```lua
Config.Mysql = "oxmysql" --(1)!
Config.MysqlTableName = "hg-auction" --(2)!
Config.MysqlTableName2 = "hg-auction_demand" --(3)!
```

1. Available options:
    - mysql-async
    - ghattimysql
    - oxmysql
2. Change the SQL Table's name (For auctions).
3. Change the SQL Table's name (For auction history).

!!! Warning
    Only change the SQL Table's name if you understand the implications!

### Auction Rules Settings
##### General rules
```lua
Config.ServerWait = 120000 --(1)!
Config.MinBet = 100 --(2)!
Config.EnableAuctionDelete = true --(3)!
Config.EnableAnimation = true -- (4)!
Config.RequiredItem = "phone" --(5)!
```

1. Amount of time between auction money refunding checks. Recommended > 30000 (In milliseconds)
2. Minimum amount above the last bid.(Minimum value is 1)
3. Allow auction deletion. (`#!lua true` or `#!lua false`)
4. Enable tablet animation when opening the interface. (`#!lua true` or `#!lua false`)
5. Item required to open the interface (item name or `#!lua false` to disable it)

##### Time Expansion settings
The time expansion system extends the time by a configurable amount when someone bets before the auction ends. This setting is ^^highly recommended for servers with over 64 concurrent players^^ as it prevents any player lag/desyncing issues.
```lua
Config.ExpandDuration = true --(1)!
Config.ExpandWhenLeft = 60 --(2)!
Config.ExpandTime = 60 --(3)!
```

1. Enable the time expansion feature when someone bids before the specified duration. (`#!lua true` or `#!lua false`)
2. The duration (in seconds) before the end of an auction when bidding triggers time extension.
3. The amount of time (in seconds) to extend when someone bids before the specified duration.

##### Rewards
```lua
Config.ReturnMoneyIfLost = true --(1)!
Config.AutoGiveReward = true -- (2)!
```

1. Automatically give the won artice to the winning players. (Functions.lua)
2. Refund the money to players after an auction ends. (`#!lua true` or `#!lua false`)

### Notifications
```lua
Config.EnableGlobalNotification = true --(1)!
Config.EnableNewAuctionNotif = true --(2)!
-- You can change/translate the notifications/Text that show up.
Config.NoBidder = "No one" --(3)!
Config.AuctionAdded = "Auction Added"
Config.AuctionUpdated = "Auction Updated"
Config.AuctionDeleted = "Auction Deleted"
Config.NotEnoughMoney1 = "You Do not have enough dirty money to place this bid"
Config.NotEnoughMoney2 = "You Do not have enough money to place this bid"
Config.BidPlaced = "Bid successfully placed"
Config.AmountDebited = "Amount Debited: " -- (4)!
Config.NotEnoughMargin = "Bid Amount should be at least  " .. Config.MinBet .. " higher than the last bid."
Config.AmountLow = "Amount too low"
Config.RefundMoney = "You have been refunded from the last auction, Amount: " --(5)!
Config.RefundDirtyMoney = "You have been refunded from the last auction, Amount: " --(6)!
Config.itemrecieved = "Auction Item Recieved"
Config.weaponrecieved = "Auction Weapon Recieved"
Config.vehrecieved = "Auction Vehicle has been delivered to your Garage"
Config.houserecieved = "Auction House recieved"
Config.otherrecieved = "" 
```

1. Enable global auction announcements in chat. (`#!lua true` or `#!lua false`)
2. Enable new auction announcements in chat. (`#!lua true` or `#!lua false`)
3. Name to show when no one has bid. 
4. Amount removed from bank/dirty money account.
5. Refund for bank money.
6. Refund for dirty money.

Notification event:
```lua
Config.Notification = function(message, type) --(1)!
        if Config.Framework == "newesx" or Config.Framework == "oldesx" then
            TriggerEvent("esx:showNotification", message)
        elseif Config.Framework == "newqb" or Config.Framework == "oldqb"  then
            TriggerEvent('QBCore:Notify', message, type, 1500)
        elseif Config.Framework == "custom" then -- (2)!
            SetNotificationTextEntry("STRING")
            AddTextComponentString(message)
            DrawNotification(false, false)
        end
end
```

1. Here you can change the events for notifications.
2.  - Define your own notification event here.
    - By default, this uses GTA's notification system.

### Access Settings
```lua
Config.AuctionJob = 'police' -- (1)!
Config.AdminPermissions = { --(2)!
    "owner",
    "superadmin",
    "admin",
    "mod",
}
Config.LeoJobs = { --(3)!
    'police',
    'sheriff',
    'ambulance'
} 
```

1. The job that has rights to add/edit/delete auctions  (job name or `#!lua false` to disable it)
2. Admin roles that have the right to add/edit/delete auctions
3. Jobs that see private auctions

!!!note
    Admins have rights to add/edit/delete auctions by default

## Customization
You can change/add Themes by changing the colors in the `theme.css` file, found under `web/`.

```
.
└── hg-auction/
    └── web/
        └── theme.css
```

If the provided `theme.css` file isn't formatted, you can use an [online CSS formatter](https://codebeautify.org/css-beautify-minify){:target="_blank"} to make it readable.

## Support
If you found anything unclear, or you have any questions, you can contact us on [Discord](https://discord.com/invite/Vn3Y2CP3n8){:target="_blank"} by opening a ticket.