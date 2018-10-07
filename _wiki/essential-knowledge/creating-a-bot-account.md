---
title: Creating a Bot Account
position: 1
keywords:
- bot creation
- get token
- add bot
- bot invite link
---

## How to create a bot and get its token

**1.** Open [https://discordapp.com/developers/applications/me](https://discordapp.com/developers/applications/me) and click on "Create an application".

>![](/img/tutorials/create-bot-account/create-application.png){:draggable="false"}

**2.** Switch to `Bot`

> If you want to, you can rename your application first

>![](/img/tutorials/create-bot-account/click-bot.png){:draggable="false"}

**3.** Click on `Add bot` and confirm the popup

>![](/img/tutorials/create-bot-account/add-bot.png){:draggable="false"}
>![](/img/tutorials/create-bot-account/confirm.png){:draggable="false"}

**4.** Copy the bot's token. In this case the token would be `NDc[...]pCs`. You can just click on `Copy`.

> This token is used to login your bot. Keep it secret!

>![](/img/tutorials/create-bot-account/copy-token.png){:draggable="false"}

**5.** If you want to, you can change the bot's name and avatar on this page, too.

## How to add a bot to your server

### Use Javacord to create the invite link

You can use Javacord to create the invite for you by simply doing:
```java
DiscordApi api = new DiscordApiBuilder().setToken("your token").login().join();
System.out.println(api.createBotInvite());
```

As an alternative, you can also create the invite link manually.

### Create the invite link manually

#### Get the client id

In order to add a bot to your server you need its client id.

You can get your client id from the [same page](https://discordapp.com/developers/applications/me) where you created it.

>![](/img/tutorials/create-bot-account/get-client-id.png){:draggable="false"}

With this id you can create an invite link for your bot.

If you are the owner or admin of the server, you can use this link to add your bot to your server. Otherwise, you have to give the link to the server owner/admins and ask them to add your bot.

> Unlike the token, you don't have to keep your client id secret

#### Create the url

Just use the following link and replace `123456789` with your own client id.

**https://discordapp.com/api/oauth2/authorize?client_id=123456789&scope=bot&permissions=0**

You can calculate the permissions (in the link above it's the `0`) on the page where you created the bot:

>![](/img/tutorials/create-bot-account/calculate-permissions.png){:draggable="false"}

## Use the invite link

You can now open the link and add the bot to your server:
>![](https://i.imgur.com/C8mzkNP.png){:draggable="false"}
