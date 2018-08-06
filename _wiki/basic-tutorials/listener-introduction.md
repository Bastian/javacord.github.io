---
title: Listener Introduction
position: 3
keywords:
- creating listeners
- listener creation
- LstenerManager
- removeListener
- remove listener
---
# Creating listeners

Creating listeners is extremely easy in Javacord. You can either use Java 8's lambda expressions to register listeners or just create a new class for them, if putting them into a method would get too messy.

## Inline Listeners

```java
api.addMessageCreateListener(event -> {
    Message message = event.getMessage();
    if (message.getContent().equalsIgnoreCase("!ping")) {
      event.getChannel().sendMessage("Pong!");
    }
});
```

## In their own class

```java
api.addListener(new MyListener());
```
and
```java
public class MyListener implements MessageCreateListener {

    @Override
    public void onMessageCreate(MessageCreateEvent event) {
        Message message = event.getMessage();
        if (message.getContent().equalsIgnoreCase("!ping")) {
            event.getChannel().sendMessage("Pong!");
        }
    }

}
```

## Object listeners

Another cool feature is the ability to attach listeners directly to objects. An example where this can be useful is, for example, reacting to reactions. The following code would delete the message if someone adds a :thumbsdown: reaction.

```java
message.addReactionAddListener(event -> {
    if (event.getEmoji().equalsEmoji("👎")) {
        event.deleteMessage();
    }
}).removeAfter(30, TimeUnit.MINUTES);
```
> Seems like the bot is very sensitive to criticism.

# Removing listeners

There are two ways to remove a listener:

## Using the returned ListenerManager

Every time you register a listener, a `ListenerManager` is returned which can be used to unregister the listener:
```java
ListenerManager<MessageCreateListener> listenerManager = api.addMessageCreateListener(event -> {
    // Do stuff
});

listenerManager.remove();
```

This manager also has some utility methods. You can, for example, remove a listener after a given time, which can be useful for object listeners:
```java
message.addReactionAddListener(event -> {
  // Do stuff
}).removeAfter(30, TimeUnit.MINUTES);
```

## Using the `removeListener(...)` method

You can remove any listener using the `removeListener(...)` method:
```java
MyListener listener = new MyListener();
api.addListener(listener);
// ...
api.removeListener(listener);
```
