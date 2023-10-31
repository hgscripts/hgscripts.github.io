---
title: Installation
description: Installation guide for HG Gearbox System
icon: fontawesome/solid/download
---
# HG-Gearbox Installation Guide

## Step 1 - Execute SQL
Included with the package you downloaded, you'll find a `hg-gearbox.sql` file

```sql title="hg-gearbox.sql"
CREATE TABLE IF NOT EXISTS `hg-gearbox` (
  `identifier` varchar(65) DEFAULT NULL,
  `data` longtext DEFAULT NULL,
  UNIQUE KEY `identifier` (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```
Use your prefered SQL client ([HeidiSQL](https://www.heidisql.com/){:target="_blank"}/[phpmyadmin](https://www.phpmyadmin.net/){:target="_blank"}/...) to execute the SQL onto your database. After inserting, make sure the table exists and the identifier's length is above 65.
## Step 2 - Add script to resouces folder
Add the script to the FiveM resources folder
```
.
└── FiveM Server/
    └── resources/
        └── [...]/
            └── hg-gearbox/
                ├── fxmanifest.lua
                └── ...
```

!!! warning
    Don't change the resource's name as it may cause some problems.

## Step 3 - Start the resouce
Add the resouce to your `server.cfg`
```ruby title="server.cfg"
ensure hg-gearbox 
```

## Step 4 (Optional) - Change configuration
Configure the script to your liking. Open `config.lua` in your prefered text editor and change the default values.
You can find a detailed explanation of the available options in the Configuration
<div class="grid cards" style="margin: 0 auto;" markdown>
-   :fontawesome-solid-gear:{ .lg .middle } __Configuration__

    ---
    Detailed documentation for available configuration options

    [:octicons-arrow-right-24: Configuration](configuration.md)
</div>
