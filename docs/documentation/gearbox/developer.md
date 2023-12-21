---
title: Developer guide
description: Developer guide (Exports) for HG-Gearbox
icon: material/dev-to
---

# HG-Gearbox Developer guide
!!! note
    All of the events are client side

## Getters

**GetSelectedGear** - Returns the currently seleted gear
```lua
-- Returns: int
exports['hg-gearbox']:GetSelectedGear()
```

**GetSelectedGearType** - Get the type of the currently selected gear.
```lua
-- Returns: string: "manual" / "auto" / "manualmoto" / "automoto"
exports['hg-gearbox']:GetSelectedGearType()
```

**GetNumberOfGears** - Get the total number of gears in the current gearbox.
```lua
-- Returns: int
exports['hg-gearbox']:GetNumberOfGears()
```

**GetSportModeStatus** - Check if the sport mode is activated.
```lua
-- Returns: boolean
exports['hg-gearbox']:GetSportModeStatus()
```

**GetClutchStatus** - Check the status of the clutch.
```lua
-- Returns: boolean
exports['hg-gearbox']:GetClutchStatus()
```

**GetUserSettings** - Get user-specific gearbox settings.
```lua
-- Returns: object
exports['hg-gearbox']:GetUserSettings()
```
Example of a returned object:
```lua
{
    manual = {
        alwaysShown = true,
        enableShake = true,
        showRPM = config.showRPM,
        scale = 1,
        knob = { alt= "Default", src= "./assets/knobs/knobM.png"},
        posx = -1,
        posy = -1,
    },
    auto = {
        alwaysShown = true,
        scale = 1,
        posx = -1,
        posy = -1,
    },
    moto = {
        scale = 1,
        posx = -1,
        posy = -1,
        manualMode = true,
    },
    misc = {
        enableSound = true,
        opacity = 1,
        volume = 0.2,
        manualMode = config.defaultgearboxtype,
    },
    theme = "default",
}
```

## Setters

**GearboxSystemStatus(status)** - Activate/Deactivate the gearbox system.
```lua
-- status: boolean
exports['hg-gearbox']:GearboxSystemStatus(status) --(1)!
```

1.  - `true`: The gearbox system is activated
    - `false`: The gearbox system is deactivated (Goes back to normal GTA behaviour)

**RefreshGearbox()** - Refresh the gearbox system.
```lua
exports['hg-gearbox']:RefreshGearbox()
```


**ForceGearboxMod(val)** - Force a specific gearbox mode: "auto" / "manual" or deactivate with false.
```lua
--val: string/false ("manual"/"auto"/false)
exports['hg-gearbox']:ForceGearboxMod(val)
```