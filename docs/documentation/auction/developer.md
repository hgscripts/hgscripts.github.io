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
