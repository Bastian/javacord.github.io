---
title: Creating Channels, Invites, etc.
position: 1
keywords:
- builder
- creating entities
- create entities
- entity creation
- create channels
- channel creation
- create webhooks
- webhook creation
- create invites
- invite creation
- create server
- server creation
---

Javacord provides `XyzBuilder` classes to create new Discord entities like channels, webhooks, servers, etc.

## Create Channels

You can get the channel builders for a specific server using the `createXyzChannelBuilder` or directly calling the constructor, e.g. creating a `ServerVoiceChannel` would look like this:
```java
Server server = ...;
new VoiceChannelBuilder(server)
    .setName("example-channel")
    .setUserlimit(10)
    .create();
```

## Create Webhooks

You can get the `WebhookBuilder` for a specific text channel:
```java
ServerTextChannel channel = ...;
new WebhookBuilder(channel)
    .setName("Captain Hook")
    .setAvatar(new File("C:/Users/Bastian/Pictures/puppy.jpg"))
    .create();
```

## Create Invites

You can get the `InviteBuilder` for a specific server channel:
```java
ServerTextChannel channel = ...;
new InviteBuilder(channel)
    .setMaxAgeInSeconds(60*60*24)
    .setMaxUses(42)
    .create();
```

## Create Servers

You can get the `ServerBuilder` from the current api instance:
```java
DiscordApi api = ...;
new ServerBuilder(api)
    .setName("My Awesome Server")
    .setIcon(api.getYourself().getAvatar())
    .setVerificationLevel(VerificationLevel.HIGH)
    .setDefaultMessageNotificationLevel(DefaultMessageNotificationLevel.ONLY_MENTIONS)
    .setRegion(Region.EU_CENTRAL)
    .create();
```
> Note: By default, bots can only create servers if they are in less than 10 servers. You can contact the Discord support to request a higher limit.
