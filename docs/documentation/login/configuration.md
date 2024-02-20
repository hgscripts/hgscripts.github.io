---
title: Configuration
description: Configuration documentation for HG Login System
icon: fontawesome/solid/gear
---
# HG-Login Configuration Documentation

## Interface Settings
We offer two different interfaces which you can switch between from **fxmanifest.lua:1**
```lua
local ui_type = "new"--(1)!
```

1. Available options:
    - "new" for new interface (2024 Update)
    - "legacy" for legacy interface (V3)


???note
    Changing interface requires Server Restart.

???tip
    Both interfaces are unlocked and can be edited.

## Config.lua

### General Settings

```lua
Config.ServerName = "servername" --(1)!
Config.IsWhitelistEnabled = true --(2)!
config.Mysql = "oxmysql" --(3)!
```

1. Your server name (required for emails)
2. Is Whitelist system enabled? (`#!lua true` or `#!lua false`)
3. Available options:
    - mysql-async
    - ghattimysql
    - oxmysql

### Discord Webhook Settings

```lua
Config.register = '' --(1)!
Config.login = '' --(2)!
Config.verfy = '' --(3)!
Config.PasswordReset = '' --(4)!
Config.registertitle = 'User registered a new account' --(5)!
Config.logintitle = 'User logged in' --(6)!
Config.verifytitle = 'User verified email' --(7)!
Config.passwordrestitle = 'User requested Password Reset' --(8)!
```

1. Webhook URL for user registration notifications.
2. Webhook URL for user login notifications.
3. Webhook URL for user email verification notifications.
4. Webhook URL for user password reset notifications.
5. Title for the webhook notification when a user registers a new account.
6. Title for the webhook notification when a user logs in.
7. Title for the webhook notification when a user verifies their email.
8. Title for the webhook notification when a user requests a password reset.

!!!note
    Make sure to replace the empty strings ('') with the actual webhook URLs you want to use for each notification type. Additionally, customize the titles to suit your preference for the webhook notifications.

### Whitelist Settings

```lua
Config.BotToken = "YOUR_BOT_TOKEN_HERE" --(1)!
Config.WebHook = "YOUR_DISCORD_WEBHOOK_HERE" --(2)!
Config.ChannelID = "YOUR_TEXT_CHANNEL_ID_HERE" --(3)!
Config.WaitEveryTick = 2000 --(4)!
```

1. Your Discord Bot Token, required for the whitelist system to function. Replace the placeholder with your actual Discord Bot Token.
2. Discord Webhook URL used for communication related to the whitelist system. Replace the placeholder with your actual Discord Webhook URL.
3. Discord Channel ID where the whitelist bot will operate. Replace the placeholder with your actual Discord Channel ID.
4. Time in milliseconds needed for the bot to read commands. Adjust this value based on your server's requirements.

!!! note
    To properly configure the Whitelist System and Discord Bot section, please follow the installation guide in the [installation section](../installation/#step-5-required-if-you-set-whitelist-to-true-discord-integration). The guide provides step-by-step instructions to ensure accurate setup.

### Translation
You can easily translate/change the notifications & email subjects
```lua
Config.ResetEmailSubject = "Account Verification - " .. Config.ServerName --(1)!
Config.PassResetEmailSubject = "Password Reset - " .. Config.ServerName --(2)!
Config.PassUpdatedEmailSubject = "Password Updated - " .. Config.ServerName --(3)!
Config.WhitelistEmailSubject = "Account whitelisted! - " .. Config.ServerName --(4)!
Config.EmailCoolDown = "Failed to Send Email, Cooldown in seconds: " --(5)!
Config.FillAllFields = "Please fill all the fields!" --(6)!
Config.Passworddontmatch = "New passwords don't match!" --(7)!
Config.FillUserOrEmail = "Please fill your username or email first!" --(8)!
Config.NoIdentifier = "No account associated with your identifier" --(9)!
Config.RegisterFirst = "Please register first" --(10)!
Config.SuccLogin = "You have logged in successfully" --(11)!
Config.VerifEmailFirst = "You need to verify your email first" --(12)!
Config.WrongLogin = "Wrong username or password" --(13)!
Config.SuccRegister = "You have registered successfully!" --(14)!
Config.EmailSent = "You should receive an email with your registration code shortly" --(15)!
Config.FailedToRegister = "Failed to register" --(16)!
Config.UserExists = "This username already exists!" --(17)!
Config.DiscordExists = "Discord account already exists!" --(18)!
Config.EmailExists = "This email address already exists!" --(19)!
Config.IdentifierExists = "There is already an account associated with your identifier!" --(20)!
Config.AlreadyVerified = "You are already verified" --(21)!
Config.SuccVerified = "You successfully verified your email" --(22)!
Config.IncorrectPIN = "Incorrect pin" --(23)!
Config.Emailresetsent = "You will shortly receive a password reset email to" --(24)!
Config.Emailusernotfound = "Email or username not found" --(25)!
Config.BadInfo = "Please check your info and try again!" --(26)!
Config.identifiermissmuch = "Identifier doesn't match!" --(27)!
Config.WrongTempPass = "Wrong temporary password" --(28)!
Config.SuccPassChange = "Password successfully changed" --(29)!
Config.pleaselogin = "Please Login" --(30)!
Config.ResentEmail = "You should receive an email to" --(31)!
Config.NotWhitelisted = "You are not whitelisted!" --(32)!
Config.LeaveMessage = "You successfully left the server" --(33)!
```

1. Account Verification email subject.
2. Password Reset email subject.
3. Password Updated email subject.
4. Whitelist Notification email subject.
5. Notification for failed email sending cooldown.
6. Notification for missing information in the registration form.
7. Notification when new passwords don't match during registration.
8. Notification to fill either username or email during login.
9. Notification when no account is associated with the provided identifier.
10. Notification prompting to register first.
11. Notification for successful login.
12. Notification to verify email first before logging in.
13. Notification for wrong username or password during login.
14. Notification for successful registration.
15. Notification about the upcoming email with registration code.
16. Notification for failed registration.
17. Notification for an existing username during registration.
18. Notification for an existing Discord account during registration.
19. Notification for an existing email address during registration.
20. Notification when there is already an account associated with the identifier.
21. Notification when the user is already verified.
22. Notification for successful email verification.
23. Notification for incorrect PIN during the whitelisting process.
24. Notification about the upcoming password reset email.
25. Notification for email or username not found during password reset.
26. Notification for incorrect information during password reset.
27. Notification when the provided identifier doesn't match.
28. Notification for a wrong temporary password during the whitelisting process.
29. Notification for successful password change.
30. Notification prompting to log in.
31. Notification about the upcoming email for various purposes.
32. Notification when the user is not whitelisted.
33. Notification for successfully leaving the server.
