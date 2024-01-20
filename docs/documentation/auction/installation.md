---
title: Installation
description: Installation guide for HG Auction System
icon: fontawesome/solid/download
---
# HG-Auction Installation Guide

## Step 1 - Execute SQL
Included with the package you downloaded, you'll find a `database.sql` file

```sql title="database.sql"
CREATE TABLE IF NOT EXISTS `hg-auction` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `auctionname` varchar(255) DEFAULT NULL,
  `price` int(11) DEFAULT NULL,
  `category` varchar(255) DEFAULT NULL,
  `starttime` varchar(255) DEFAULT NULL,
  `endtime` varchar(255) DEFAULT NULL,
  `isprivate` int(11) NOT NULL DEFAULT 0,
  `isblackmoney` int(11) NOT NULL DEFAULT 0,
  `img` varchar(1000) DEFAULT '',
  `plate` varchar(255) DEFAULT NULL,
  `itemname` varchar(255) DEFAULT NULL,
  `propertyid` int(50) DEFAULT NULL,
  `shellid` int(50) DEFAULT NULL,
  `lastbetowner` varchar(65) DEFAULT NULL,
  `lastbet_identifier` varchar(65) DEFAULT NULL,
  `lastprice` int(11) DEFAULT NULL,
  `ended` int(11) DEFAULT 0,
  `deleted` int(11) DEFAULT 0,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8;


CREATE TABLE IF NOT EXISTS `hg-auction_demand` (
  `auction_id` int(11) DEFAULT NULL,
  `user_identifier` varchar(255) DEFAULT NULL,
  `user_price` int(11) DEFAULT NULL,
  `ended` int(11) DEFAULT 0,
  `iswinner` int(11) DEFAULT 0,
  `isblackmoney` int(11) DEFAULT 0
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
Use your prefered SQL client ([HeidiSQL](https://www.heidisql.com/){:target="_blank"}/[phpmyadmin](https://www.phpmyadmin.net/){:target="_blank"}/...) to execute the SQL onto your database.

## Step 2 - Add script to resouces folder
Add the script to the FiveM resources folder
```
.
└── FiveM Server/
    └── resources/
        └── [...]/
            └── hg-auction/
                ├── fxmanifest.lua
                └── ...
```

!!! warning
    Don't change the resource's name as it may cause some problems.

## Step 3 - Start the resouce
Add the resouce to your `server.cfg`
```ruby title="server.cfg"
ensure hg-auction
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
