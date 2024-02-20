---
title: Installation
description: Installation guide for HG Login System
icon: fontawesome/solid/download
---
## Step 1 - Execute SQL
Included with the package you downloaded, you'll find a `database.sql` file

```sql title="database.sql"
CREATE TABLE IF NOT EXISTS `hg_login` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `email` varchar(30) CHARACTER SET utf8mb4 NOT NULL,
  `username` varchar(20) CHARACTER SET utf8mb4 NOT NULL,
  `password` text CHARACTER SET utf8mb4 NOT NULL,
  `identifier` text CHARACTER SET utf8mb4 NOT NULL,
  `discord` varchar(20) CHARACTER SET utf8mb4 NOT NULL,
  `pin` int(11) DEFAULT NULL,
  `verified` int(1) unsigned zerofill DEFAULT 0 NOT NULL,  -- Default to 0
  `temppass` text CHARACTER SET utf8mb4 DEFAULT NULL,
  `whitelisted` int(1) unsigned zerofill DEFAULT 0 NOT NULL,  -- Default to 0
  KEY `uid` (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=42 DEFAULT CHARSET=latin1;
```
Use your prefered SQL client ([HeidiSQL](https://www.heidisql.com/){:target="_blank"}/[phpmyadmin](https://www.phpmyadmin.net/){:target="_blank"}/...) to execute the SQL onto your database.

## Step 2 - Add script to resouces folder
Add the script to the FiveM resources folder
```
.
└── FiveM Server/
    └── resources/
        └── [...]/
            └── hg-login/
                ├── fxmanifest.lua
                └── ...
```

!!! warning
    Don't change the resource's name as it may cause some problems.

## Step 3 - Start the resouce
Add the resource to your `server.cfg` (first script)
```ruby title="server.cfg"
ensure hg-login
```
!!! warning
    Ensure that 'hg-login' is the first resource listed in your server.cfg file.

## Step 4 (Optional) - Change configuration
Configure the script to your liking. Open `config.lua` in your prefered text editor and change the default values.
You can find a detailed explanation of the available options in the Configuration
<div class="grid cards" style="margin: 0 auto;" markdown>
-   :fontawesome-solid-gear:{ .lg .middle } __Configuration__

    ---
    Detailed documentation for available configuration options

    [:octicons-arrow-right-24: Configuration](configuration.md)
</div>

## Step 5 (Required if you set whitelist to true) - Discord Integration

To enable Discord integration and set up your whitelist manager, follow these steps:

1. Create a text channel in your Discord server.
2. Make a webhook for the text channel and paste it into the `Config.WebHook` field.
3. Copy the text channel ID and paste it into the `Config.ChannelID` field.
4. Create a Discord bot and invite it to your server. Ensure the bot has read permissions for the created text channel.
5. Paste your Discord bot token into the `Config.BotToken` field.
6. Make sure to check the "MESSAGE CONTENT INTENT" inside your Discord bot application [here](https://discord.com/developers/applications/).

Here is an example configuration in your `hg-login/config.lua`:

```lua
Config.BotToken = "YOUR_BOT_TOKEN_HERE"
Config.WebHook = "YOUR_DISCORD_WEBHOOK_HERE"
Config.ChannelID = "YOUR_TEXT_CHANNEL_ID_HERE"
Config.WaitEveryTick = 2000 -- Time needed for the bot to read commands
```


