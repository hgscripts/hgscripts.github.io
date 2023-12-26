---
title: Developer Guide
description: Developer guide for HG Wanted System
icon: material/dev-to
---

# HG-Wanted Developer Guide

The HG-Wanted script provides a set of exports that allow you to interact with the wanted system. Here's how you can use them:

## Set Wanted Status

You can set a player's wanted status using the `SetWanted` export.

```lua
exports['hg-wanted']:SetWanted(playerId)
```

## Remove Wanted Status
You can remove a player's wanted status using the `RemoveWanted` export. 
```lua
exports['hg-wanted']:RemoveWanted(playerId)
```

## Check Wanted Status
You can check if a player is wanted using the `CheckWanted` export.
```lua
local isWanted = exports['hg-wanted']:CheckWanted(playerId)
```
This will return true if the player with the given playerId is wanted, and false otherwise.
