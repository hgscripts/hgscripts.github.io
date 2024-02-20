---
title: Developer Guide
description: Developer guide for HG Notify System
icon: material/dev-to
---

# HG-Notify Developer Guide

The HG-Notify script provides a set of exports that allow you to send notifications to players. Here's how you can use them:

## Client Side

You can display a notification using the `ToggleNotify` export from **client side**.

```lua
exports['hg-notify']:ToggleNotify({
            status = "success", --(1)!
            title = "Success", --(2)!
            text = "This is a success notification", --(3)!
            audio = "success", -- optional --(4)!
            effect = "slide", -- optional --(5)!
            speed = 300, -- optional --(6)!
            customClass = "", -- optional --(7)!
            showIcon = true,  --(8)!
            autotimeout = 3000,-- optional --(9)!
            type = "outline", -- optional --(10)!
            position = "right top", -- optional --(11)!
            gap = 20, -- optional --(12)!
            padding = 20  -- optional --(13)!
})
```

1. Notification type : `'error'` || `'warning'` || `'success'` || `'info'` 
2. Notification title (obviously)
3. Notification body text (you can use html)
4. Notification Sound: `'error'` || `'warning'` || `'success'` || `'info'` 
5. Notificaiton Effect: `'fade'`|| `'slide'`
6. transition-duration in milliseconds
7. Css class
8. Show Notification icon ? (`#!lua true` or `#!lua false`)
9. Notification duration in milliseconds
10. Notification Style: `'outline'` || `'filled'`
11. Notification position: Combine x and y position. `'left'`, `'right'`, `'top'`, `'bottom'`, `'x-center'`, `'y-center'` or use only `'center'` to center both x and y
12. Gap between notifications
13. Padding of the notifications


You can force clear all notification using the `ClearNotify` export from **client side**.

```lua
exports['hg-notify']:ClearNotify() --(1)!
```

1. Force close all notifications

## Server Side

You can display a notification for a specific player using the `ToggleNotify` export from **server side**.

```lua
exports['hg-notify']:ToggleNotify(source, {
            status = "success", --(1)!
            title = "Success", --(2)!
            text = "This is a success notification", --(3)!
            audio = "success", -- optional --(4)!
            effect = "slide", -- optional --(5)!
            speed = 300, -- optional --(6)!
            customClass = "", -- optional --(7)!
            showIcon = true,  --(8)!
            autotimeout = 3000,-- optional --(9)!
            type = "outline", -- optional --(10)!
            position = "right top", -- optional --(11)!
            gap = 20, -- optional --(12)!
            padding = 20  -- optional --(13)!
})
```

1. Notification type : `'error'` || `'warning'` || `'success'` || `'info'` 
2. Notification title (obviously)
3. Notification body text (you can use html)
4. Notification Sound: `'error'` || `'warning'` || `'success'` || `'info'` 
5. Notificaiton Effect: `'fade'`|| `'slide'`
6. transition-duration in milliseconds
7. Css class
8. Show Notification icon ? (`#!lua true` or `#!lua false`)
9. Notification duration in milliseconds
10. Notification Style: `'outline'` || `'filled'`
11. Notification position: Combine x and y position. `'left'`, `'right'`, `'top'`, `'bottom'`, `'x-center'`, `'y-center'` or use only `'center'` to center both x and y
12. Gap between notifications
13. Padding of the notifications


## Variables Table

| Parameter             | Type    | Values                                   | Default |
| :--------------------- | :------ | :----------------------------------------| :-----: |
| `status`              | String  | `'error'`, `'warning'`, `'success'` `'info'` | `null`  |
| `title`               | String  |                                          | `null`  |
| `text`                | String  | You can send any type of HTML.           | `null`  |
| `audio`               | String  | Audio path: ui/assets/                   | `null`  |
| `customIcon`          | String  | You can send any type of HTML.           | `null`  |
| `customClass`         | String  |                                          | `null`  |
| `speed`               | Number  | Transition duration in milliseconds.    | `300`   |
| `effect`              | String  | `'fade'`, `'slide'`                      | `'fade'`|
| `showIcon`            | Boolean |                                          | `true`  |
| `showCloseButton`     | Boolean |                                          | `true`  |
| `autoclose`           | Boolean |                                          | `true`  |
| `autotimeout` (with `autoclose: true`) | Number  |                                   | `3000`  |
| `gap` (margin between notifications) | Number  |                                  | `20`    |
| `distance` (distance to edges)       | Number  |                                  | `20`    |
| `type`                | String  | `'outline'`, `'filled'`                  | `'outline'`|

