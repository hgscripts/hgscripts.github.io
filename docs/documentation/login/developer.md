---
title: Developer Guide
description: Developer guide for HG Login System
icon: material/dev-to
---

# HG-Login Developer Guide

## Testing / Debugging

You can use the following configuration options during development to aid debugging and testing

```lua
-- For Dev
Config.EmailDebug = false --(1)!
Config.EnableTestingCommands = false --(2)!
```

1. Enable email service API debug mode (Server Console). This helps troubleshoot email-related functionalities during development (`#!lua true` or `#!lua false`)

2. Enable testing commands, allowing simulation of various scenarios in the server console.
   Usage: (server console)
     - testemail register email@email.com
     - testemail passreset email@email.com
     - testemail passchanged email@email.com
     - testemail whitelist email@email.com

## Email Customization


You can customize the existing letters for each email by changing `Whitelist.html`, `Register.html`, `PasswordReset.html`, `PasswordChanged.html` files, found under `letters/`.

```
.
└── hg-login/
    └── letters/
        └── Whitelist.html
        └── Register.html
        └── PasswordReset.html
        └── PasswordChanged.html
```

You can download the html letters below
<div class="grid cards" markdown>
-   [:fontawesome-solid-download:{ .lg .middle } __Download Whitelist.html__](assets/Whitelist.html){:download="Whitelist.html"}
-   [:fontawesome-solid-download:{ .lg .middle } __Download Register.html__](assets/Register.html){:download="Register.html"}
-   [:fontawesome-solid-download:{ .lg .middle } __Download PasswordReset.html__](assets/PasswordReset.html){:download="PasswordReset.html"}
-   [:fontawesome-solid-download:{ .lg .middle } __Download PasswordChanged.html__](assets/PasswordChanged.html){:download="PasswordChanged.html"}
</div>


!!! Warning
    We only allow **imgur** and **discord** links in email html letters, if you use different links, the emails will not be delivered.

!!! Info
    Look for server side print on resource start to know if the letters got imported successfully or no.

