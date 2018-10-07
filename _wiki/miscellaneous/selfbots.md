---
title: Client Account Bots (Selfbots)
position: 3
keywords:
- Good way to get banned
---

Javacord supports logging in with "real" accounts instead of the normal bot accounts (sometimes also called "selfbots"). However, there are some risks involved with client accounts.

## ❗ Disclaimer ❗

### You are risking a ban

Selfbots violate [Discord's terms of service](https://discordapp.com/terms) and using this "feature" will very likely result in a ban of your account.

### Something might break

Client accounts are very similar to bot accounts, but there are some small (undocumented) differences, and Discord changes the client api from time to time without telling us. This means that the same code that worked fine yesterday might no longer work today and break your bot. Fixing these issues is not a priority for Javacord, so in the worst case your bot might not work for several days.

### Not all features are supported

Javacord's main focus is on bot accounts and logging in with client accounts only exists, because it was very easy to support. Many client-only features (e.g. private/group channel calls) are not supported by Javacord and maybe never will be.

### We might remove this feature

As client accounts violate Discord's TOS, we might completely remove this feature one day. At the moment it's pretty easy to maintain support for client accounts, but if Discord starts taking action (e.g. by adding captchas) against selfbots and it would be an unreasonable amount of work to support the client account feature, we will just completely remove it.

If Discord's going to ask us (or all libraries in general) to remove this feature, we will very likely accept their request.

## Logging In With a Client Account

### Getting the token

If you are willing to accept the risks involved in using a selfbot, you first need to get the token of your account.
You can get it by pressing `Ctrl` + `Shift` + `i` and navigating to `Network`.
Filter the request type to only display `XHR` requests and search for a request that contains an `authorization` request header.
If you don't see any requests, just press `Ctrl` + `r`. In this example, the token would be `mfa.h[...]c5eu`.

![](/img/tutorials/selfbots/get-client-token.png){:draggable="false"}

### Using the token

Logging in to client accounts is very similar to normal bot accounts:
```java
DiscordApi api = new DiscordApiBuilder()
    .setAccountType(AccountType.CLIENT)
    .setToken("your token")
    .login().join();
System.out.println("Logged in!");
```