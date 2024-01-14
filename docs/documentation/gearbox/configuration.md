---
title: Configuration
description: Configuration documentation for HG Gearbox System
icon: fontawesome/solid/gear
---
# HG-Gearbox Configuration Documentation

## Config.lua
### General Settings
#### Language Settings
Change the language to any of the provided locales
```lua
config.Language = "en" --(1)!
```

1. Provided Languages:

    | Value    | Language           |
    | -------- | ---------------------- |
    | **ar**   | Arabic                 |
    | **de**   | German                 |
    | ==**en**==   | English                |
    | **es**   | Spanish                |
    | **fi**   | Finnish                |
    | **fr**   | French                 |
    | **is**   | Icelandic              |
    | **it**   | Italian                |
    | **pt-br**| Brazilian Portuguese   |
    | **pt**   | Portuguese              |
    | **sw**   | Swedish                |
    | **vn**   | Vietnamese              |

You can add a language or modify an existing one very easily. Simply navigate to the `ui/assets/locale` directory:
```
.
└── hg-gearbox/
    └── ui/
        └── assets/
            └── locale/
                ├── en.json
                └── *.json
```
There, you'll find json files that have the translations for the panel. You can modify the existing ones. To add another language, simply copy one of the existing files (ex: `en.json`) and rename it to something else (ex: `tr.json` for Turkish) And change the text.

Example:
<div class="grid" markdown>

```json title="en.json"
{
    "SAVEANDCLOSE":"Save & Close",
    "MANUALGEARBOX": "Manual Gearbox",
    "SHOWRPM":"Show RPM",
    // Rest of the file
}
```

```json title="tr.json"
{
    "SAVEANDCLOSE": "Kaydet ve Kapat",
    "MANUALGEARBOX": "Manuel Şanzıman",
    "SHOWRPM": "RPM Göster",
    // Rest of the file
}
```

</div>

Next, simply change the value to whatever you named the file 
```lua
config.Language = "tr"
```

#### General controls
```lua hl_lines="2"
config.invertcontrolinreverse = true -- (1)!
config.clutchbutton = 21 -- (2)!
config.gearsettingscommand = 'gearmenu' --(3)!
```

1. Invert the control of the ACCELERATE (++w++) and BRAKE (++s++) keys when in Reverse. 
    - This setting applies to all the gearboxes.
2. The button for toggling the clutch. 
    - By Default: ++shift++
    - ^^**This setting applies to all the gearboxes.**^^
3. Define the command to open the gear settings menu.

#### SQL Settings
```lua
config.Mysql = "oxmysql" --(1)!
config.MysqlTableName = "hg-gearbox" --(2)!
```

1. Available options:
    - mysql-async
    - ghattimysql
    - oxmysql
2. Change the SQL Table's name.

!!! Warning
    Only change the SQL Table's name if you understand the implications!

#### Gameplay Settings
```lua
config.enableanimation = true -- (1)!
config.defaultgearboxtype = false -- (2)!
config.switchgeartype = true --(3)!
config.showRPM = true -- (4)!
config.EngineKill = true -- (5)!
```

1. Enable the gear changing animation.
2. Set the default gearbox type:
    - If set to `#!lua true`, it will default to the **Manual** Gearbox
    - If set to `#!lua false`, it will default to the **Automatic** Gearbox

3.  Allow players to switch between gearbox types from the settings panel.
4.  Enable RPM meter next to manual gearbox by default.
5.  Kill the engine when putting the vehicle in high gear and starting to roll for a realistic experience.

#### Vehicle Blacklist/Whitelist
The vehicle classes set below will function normally without the gearbox system.
You can find a list of the vehicle categories in the [FiveM Docs](https://docs.fivem.net/natives/?_0x29439776AAA00A62){:target="_blank"}
```lua
config.blacklistedvehicleclasses = {13, 14, 15, 16, 21}
```
Vehicle models set below will function normally without a gearbox system.
```lua
config.blacklistedvehicles = {"faggio", "faggio2", "faggio3"}
```

Specify vehicles that are forced to be automatic

```lua
config.allvehiclesAreManualExcept = {
    status = false,
    'nero'
    't20'
}
```

Specify vehicles that are forced to be manual

```lua
config.allvehiclesAreAutoExcept = {
    status = false,
    'sultanrs'
    'banshee'
}
```
!!! note
    `config.AllVehiclesAreManualExcept` and `config.AllVehiclesAreAutoExcept` will override `config.defaultgearboxtype` and `config.switchgeartype`.

!!! Warning
    DO NOT enable 'config.allVehiclesAreManualExcept' and 'config.allVehiclesAreAutoExcept' simultaneously. The script will break.

Specify vehicles that are forced to use the motorcycle gearbox
```lua
config.forcemotorcycle = {
    status = false,
    'policeb',
}
```

### Manual Gearbox Settings
#### Gameplay

```lua
config.enableCarAutoRollOnDrive = true -- (1)!
config.enginebrake = true -- (2)!
config.Tranmissionmod = true -- (3)!
config.manualgearchangemethods = "both"  --(4)!
```

1. Allow the vehicle to start rolling slowly in 1st gear after releasing the clutch.
2. Enable engine braking when downshifting for a more realistic experience. (This will apply to motorcycles as well)
3. When enabled, vehicles with a modified transmission (Not stock) will get an extra gear.
4. Choose the allowed methods for changing gears. 
    - Allowed options:
        - 'both'
        - 'numpad'
        - 'pageupdown'
        - 'none'
#### Controls
##### Number Controls
```lua
config.clutchbuttons = true -- (1)!
config.changegearN = "NUMPAD0"
config.changegear1 = "NUMPAD1"
config.changegear2 = "NUMPAD2"
config.changegear3 = "NUMPAD3"
config.changegear4 = "NUMPAD4"
config.changegear5 = "NUMPAD5"
config.changegear6 = "NUMPAD6"
config.changegear7 = "NUMPAD7"
config.changegearR = "NUMPAD9"
```

1. If `true`, the clutch needs to be pressed to change gears using numbers.


##### Sequential Controls
```lua
config.clutchbuttons2 = true -- (1)!
config.changegearup = "pageup"
config.changegeardown = "pagedown"
```

1. If `true`, the clutch needs to be pressed to change gears in sequential mode.

!!! note
    Both Number and Sequential controls can be changed by the users from the GTA settings.

### Automatic Gearbox Settings
#### Gameplay
```lua
config.enableCarAutoRollOnDriveAuto = true --(1)!
```

1. Allow the vehicle to start rolling in Drive/Sport gear.
 
#### Sport Mode
```lua
config.EnableSportMode = true -- (1)!
config.SportModeEnabledForAllVehicles = false --(2)!
config.SportModeEnabledOnlyForTheseClasses = { 
    status = true, -- (3)!
    6, 7 -- (4)!
}
config.SportModeEnabledOnlyForTheseVehicles = {
    status = false, -- (5)!
    't20','nero' -- (6)!
}   

config.sportmodeDriveForce = 1.5 --(7)!
config.sportmodeTopSpeed = 1.5 --(8)!
config.sportmodeBrakeForce = 1.5 --(9)!
```

1. Enable/disable sport mode 
    - :material-alert: This will overide all the next settings if set to false.
2. Enabled Sportmode for ALL vehicles 
    - Recommended off.
    - :material-alert: This will override ^^*config.SportModeEnabledOnlyForTheseClasses*^^ & ^^*config.SportModeEnabledForTheseVehicles*^^
3. Enable Sport mode for the vehicle classes below.
4. Vehicle classes can be found in the [FiveM Documentation](https://docs.fivem.net/natives/?_0x29439776AAA00A62){:target="_blank"}.
5. Enable Sport mode only for these vehicles.
6. Put the desired vehicles seperated by a comma  `,`
7. Set drive force multiplier for sport mode. Recommended Values: 1.0-2.0
8. Set top speed multiplier for sport mode. Recommended Values: 1.0-2.0
9. Set brake force multiplier for sport mode. Recommended Values: 1.0-2.0

### Motorcycle Gearbox Settings
#### Gameplay
```lua
config.EnableMotorcycleGearBox = true -- (1)!
config.isclutchrequired = true -- (2)!
config.enableMotoAutoRollOnDrive = true  -- (3)!
config.enablegearmodeswitch = true -- (4)!
```

1. Enable or disable the gearbox for motorcycles.
2. Specify if clutch button must be pressed to change motorcycle gears.
3. Allow the motorcycle to start rolling slowly in 1st gear after releasing the clutch.
4. Allow players to switch between manual and automatic modes on motorcycles.
#### Controls
```lua
config.motogearupbutton = "ADD" -- (1)!
config.motogeardownbutton = "SUBTRACT" -- (2)!
```

1. Define Gear Up button for Motorcycles
    - By Default: Numpad PLUS (++num-plus++)
2. Define Gear Up button for Motorcycles
    - By Default: Numpad MINUS (++num-minus++)
!!!note
    Both Gear UP and Gear DOWN buttons can be changed from the GTA settings

### Notification Settings
#### Options
```lua
config.EnableNotifications = false --(1)!
config.Debug = false -- (2)!
config.Framework = "custom" -- (3)!
config.Notification = function(message, type) -- (4)!
    if config.EnableNotifications then
        if config.Framework == "esx" then
            TriggerEvent("esx:showNotification", message)
        elseif config.Framework == "qb" then
            TriggerEvent('QBCore:Notify', message, type, 1500)
        elseif config.Framework == "custom" then --(5)!
            SetNotificationTextEntry("STRING")
            AddTextComponentString(message)
            DrawNotification(false, false)
        end
    end
end
```

1. Enable alert notifications.
2. Enable debugging mode in client console.
3. Choose which framework's notification system to use.
    - Available options
        - esx
        - qb
        - custom
4. Here you can change the events for notifications.
5.  - Define your own notification event here.
    - By default, this uses GTA's notification system.
#### Customize text
```lua
config.txt1 = "Option disabled" --(1)!
config.txt2 = "This is for vehicles not for motorcycles" --(2)!
config.txt3 = "Gearbox type is forced by server owner" --(3)!
config.txt4 = "Press clutch" --(4)!
```

1. Shows up when a player tries to change a disabled option.
2. Shows up when a player tries to change between car Auto/Manual modes while on a motorcycle.
3. Shows up when a player tries to change a forced gearbox type.
4. Shows up when a player tries to change gears without pressing the clutch (When clutch is required).

## UI Customization
### Color scheme
You can customize the existing themes by changing the colors in the `themes.css` file, found under `ui/`.

```
.
└── hg-gearbox/
    └── ui/
        └── themes.css
```

If the provided `themes.css` file isn't formatted, you can use an [online CSS formatter](https://codebeautify.org/css-beautify-minify){:target="_blank"} to make it readable, or simply download the formatted themes.css below
<div class="grid cards" markdown>
-   [:fontawesome-solid-download:{ .lg .middle } __Download themes.css__](assets/themes.css){:download="themes.css"}
</div>

Each of these variables roughly describes what each color represents. Results may differ between gearboxes.

`m-01`, `m-02`,`m-03` and `g-01` are for the panel
```css
[data-theme=purple] {
    --gearboxBackgroundColor: #5042ab;
    --gateOutlineColor: #f3c150;
    --gateBackgroundColor: #000000;
    --horizontalGateBackgoundColor: #000000;
    --gearIndicatorColor: #ffffff;
    --reverseGearColor: #f3c150;
    --redlineColor: #f3c150;
    --m-01: #5042ab;
    --m-02: #776ace;
    --m-03: #c9c5f5;
    --g-01: linear-gradient(95deg, var(--m-01), var(--m-02))
}
```

???note
    You can't add more themes. You can only modify the existing  ones.
???tip
    To make sure the colors you use are visible, keep the same contrast as the default colors for each theme.

### Customize Gearknobs
You can customize the gearknobs by changing the default pictures that come with the script. You can find the pictures under `ui/assets/knobs`.

```
.
└── hg-gearbox/
    └── ui/
        └── assets/
            └── knobs/
```

There, you'll find a collection of gearknobs. Here are the knobs which are used in the manual gearbox:

| Gearknob   | File name            |
| ---------- | -------------------- |
| Default    | knobM.png            |
| Basketball | knobMBasketball.png  |
| Kuromi     | knobMKuromi.png      |
| Skull      | knobMSkull.png       |
| Finger     | knobMSkullFinger.png |
| 8Ball      | knobM8ball.png       |
| Biohazard  | knobMBiohazard.png   |
| Arcade     | knobMArcade.png      |

You can download the provided Photoshop Document (`Gearknob.psd`) where you'll find a template.

<div class="grid cards" markdown>
-   [:fontawesome-solid-download:{ .lg .middle } __Download Gearknobs.psd__](assets/Gearknobs.psd){:download"Gearknobs.psd"}
</div>

???info
    If you're going to change the shape of one of the gearknobs, make sure to keep the same resolution/aspect ratio as the original ones. Also make sure that the base of the knob is in the same position.
???info
    We don't recommend you change the shape Motorcycle's shifter, as it's very precisely placed to fit the shift light. You can make modifications to the existing one without 
???note
    You can't add more gearknobs, you have to replace the existing ones.

### Change Panel Font
You can change the panel's font by adding font files (`*.otf` / `*.ttf`/...) in the `ui/assets/fonts` folder and defining a new font family named `Custom` in the `fonts.css` file. You need font weights `400`, `500` and `700`.

Example:
```css
@font-face {
    font-family: Custom;
    src: url('../fonts/MyFont.ttf') format('truetype');
    font-weight: 400;
}
```
You can read more about font faces [here](https://www.w3schools.com/cssref/css3_pr_font-face_rule.php){:target="_blank"}. 

## Support
If you found anything unclear, or you have any questions, you can contact us on [Discord](https://discord.com/invite/Vn3Y2CP3n8){:target="_blank"} by opening a ticket.