---
title: Configuration
description: Configuration documentation for HG Wanted System
icon: fontawesome/solid/gear
---
# HG-Wanted Configuration Documentation

## Config.lua
### General settings
```lua
Config.Framework = "newqb" --(1)!
Config.Mysql = "oxmysql" --(2)!
Config.menucommand = 'wantedmenu' --(3)!
Config.menubutton = 'F9' --(4)!
Config.policejob = "police" --(5)!
Config.policejob2 = "sheriff" --(6)!
Config.EnableGlobalNotification = true --(7)!
Config.NotificationDuration = 15 --(8)!
Config.MinTimeBetweenSpots = 5 --(9)!
Config.NpcSpot = true --(10)!
Config.DisplayWantedLogo = true --(11)!
Config.NpcSpotDistance = 6 --(12)!
Config.AutoRemoveWanted = true --(13)!
Config.CanHideWithMask = true --(14)!
Config.NpcCallChance = 0.5 --(15)!

```

1. Framework to use: "newesx", "oldesx", "newqb", or "oldqb"
2. MySQL library to use: "mysql-async", "ghmattimysql", or "oxmysql"
3. Command to open the menu
4. Button to open the menu (leave blank '' if you don't want a button)
5. Name of the first police job
6. Name of the second police job
7. Enable or disable global wanted notification for all players
8. Duration of the global notification (in seconds)
9. Minimum time between each NPC spot for the wanted person (in minutes)
10. Enable or disable the NPC spotting system
11. Display the "WANTED" logo on the screen of wanted players
12. Maximum distance between the wanted player and the NPC to be spotted
13. Automatically remove wanted status when the player gets cuffed by a police officer (disabled for ESX)
14. If true, wanted players won't be recognized by NPCs when wearing a mask
15. The chance for the NPC to call the police on you (0.00-1.00)
      - (0.5 = 50% chance )

### Menu settings
#### Styling
```lua
Config.MenuStyle = "native" --(1)! 
Config.MenuSize = "size-100" --(2)!
Config.MenuLocation = "topright" --(3)!
```

1. Change the menu theme. You can choose between "native" or "default"
2. Change the menu size. You can choose between:
      - "size-100" 
      - "size-110" 
      - "size-125" 
      - "size-150" 
      - "size-175" 
      - "size-200"
3. Choose the menu position. Examples:
      - "topleft" 
      - "bottomcenter" 
      - "bottomright" 
      - "centerright" 
      - ... 

#### Text
You can easily translate/change the menu's text and icons
```lua
Config.Title = "Wanted Menu"
Config.menu1 = "Police Wanted Menu"
Config.menu2 = "Set Wanted"
Config.menu3 = "Remove Wanted"
Config.menu4 = "Wanted citizen list"
Config.menu5 = "Check wanted status"
Config.menu6 = "wanted status"
Config.menu7 = "Online Citizens"
Config.menu8 = "Online wanted citizen list"
Config.menu9 = "Nearby Citizen"
Config.icon1 = '👮'
Config.icon2 = '⛔'
Config.icon3 = '🦹‍♂️'
Config.icon4 = '⚠️' 
Config.icon5 = '✖️'
Config.icon6 = '➰'
```

### Translation
You can easily translate/change the notifications
```lua
Config.text1 = "Online Citizens"
Config.text2 = "Click to Send global notification again"
Config.text3 = "no player nearby"
Config.text4 = "This citizen is wanted"
Config.text5 = "This citizen is not wanted"
Config.text6 = "You are not a police officer or you are not in service"
Config.text12 = "You are busted"
Config.text13 = "An npc has spotted you and called the police"
Config.text14 = "Wanted person spotted"
Config.text15 = "Citizen is now wanted"
Config.text16 = "You are now wanted"
Config.text17 = "Notification Sent to citizens"
Config.text18 = "This citizen is no longer wanted"
Config.text19 = "You are no longer wanted"
Config.text20 = "Position Marked in Minimap"
```

### Discord webhooks
We provide discord webhook functionality that sends messages to a discord channel when a citizen is wanted/no longer wanted
```lua
Config.wanteddiscord = "" --(1)! 
Config.notwanteddiscord = "" --(2)!
Config.wantedtitle = "Player Wanted"
Config.notwantedtitle = "Player No longer Wanted"
```

1. Set the link of the webhook that sends out "Player WANTED" when a player is wanted.
2.  Set the link of the webhook that sends out "Player No longer WANTED" when a player's wanted status is removed.

### Ped Blacklist
Here you can set the peds who don't report wanted players (Won't spot the player)
You can find ped hashes [here](https://wiki.rage.mp/index.php?title=Peds){:target="_blank"}
```lua
Config.BlacklistedPeds = {
    --mp_freemode peds
    1885233650,
    -1667301416,
    --ANIMALS  
    -832573324,
    1462895032,
    -1430839454,
    -1469565163,
    351016938,
    1457690978,
    -50684386,
    1682622302,
    402729631,
    -664053099,
    -1950698411,
    802685111,
    1015224100,
    1794449327,
    1193010354,
    1318032802,
    -1920284487,
    307287994,
    -1323586730,
    111281960,
    1125994524,
    1832265812,
    -541762431,
    -1011537562,
    882848737,
    -1026527405,
    -1788665315,
    -745300483,
    1126154828,
    -1589092019,
    113504370,
    -1384627013 
}
```
### Notification settings
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
## Support
If you found anything unclear, or you have any questions, you can contact us on [Discord](https://discord.com/invite/Vn3Y2CP3n8){:target="_blank"} by opening a ticket.
