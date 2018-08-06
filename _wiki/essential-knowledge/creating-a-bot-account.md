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

**1.** Open [https://discordapp.com/developers/applications/me](https://discordapp.com/developers/applications/me) and click on "New App".

>![](https://i.imgur.com/tXv7YsR.png)

**2.** Enter a name for your bot and click "Create App".

>![](https://i.imgur.com/7JCZSGq.png)

**3.** Click on "Create a Bot user".

>![](https://i.imgur.com/RdTcXo2.png)

**4.** Reveal the bot's token. This token is used to authenticate your bot.

>![](https://i.imgur.com/g9d1pva.png)
>![](https://i.imgur.com/t90UBTk.png)

## How to add a bot to your server

### Get the client id

In order to add a bot to your server you need its client id.

You can get your client id from the [same page](https://discordapp.com/developers/applications/me) where you created it.

>![](https://i.imgur.com/XXEKGOP.png)

With this id you can create an invite link for your bot.

If you are the owner or admin of the server, you can use this link to add your bot to your server. Otherwise, you have to give the link to the server owner/admins and ask them to add your bot.

### Create the invite link yourself

Just use the following link and replace `123456789` with your own client id.

**https://discordapp.com/api/oauth2/authorize?client_id=123456789&scope=bot&permissions=0**

### Use Javacord to create the invite link

You can also let Javacord create the invite for you by simply doing:
```java
DiscordApi api = new DiscordApiBuilder().setToken("your token").login().join();
System.out.println(api.createBotInvite());
```

### Use a website to build the invite

You can also use an invite builder, like [this](https://finitereality.github.io/permissions-calculator/) one.

### Use the invite link

You can now open the link and add the bot to your server:
>![](https://i.imgur.com/C8mzkNP.png)
