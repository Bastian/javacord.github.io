---
title: Using the MessageBuilder
position: 5
keywords:
- create messages
- message creation
- sendMessage
---

## Introduction

The `MessageBuilder` class is an alternative to the `channel.sendMessage(...)` method, which can be used to easily format messages.

## Example

The following code
```java
new MessageBuilder()
    .append("Look at these ")
    .append("awesome", MessageDecoration.BOLD, MessageDecoration.UNDERLINE)
    .append(" animal pictures! 😃")
    .appendCode("java", "System.out.println(\"Sweet!\");")
    .addAttachment(new File("C:/Users/Bastian/Pictures/kitten.jpg"))
    .addAttachment(new File("C:/Users/Bastian/Pictures/puppy.jpg"))
    .setEmbed(new EmbedBuilder()
            .setTitle("WOW")
            .setDescription("Really cool pictures!")
            .setColor(Color.ORANGE))
    .send(channel);
```
would be displayed like this:
> ![](https://i.imgur.com/AP1cjDf.png){:draggable="false"}