---
title: Setup IntelliJ + Gradle
position: 2
---
## Setup

**1.** Start IntelliJ

**2.** Create a new project (`File` -> `New` -> `Project`)
>![](/img/tutorials/setup-intellij-gradle/create-project.png){:draggable="false"}

**3.** Select `Gradle`

**4.** Make sure to select a SDK which is 1.8 (or greater)

**5.** Click `Next`
>![](/img/tutorials/setup-intellij-gradle/select-gradle.png){:draggable="false"}

**6.** Enter a group id (e.g. `com.github.yourname`)

> You can choose whatever you want

**7.** Enter an artifact id (e.g. `myfirstbot`)

> You can choose whatever you want

**8.** Click `Next`
>![](/img/tutorials/setup-intellij-gradle/new-project.png){:draggable="false"}

**9.** Check `Use auto-import`

**10.** Click `Next`
>![](/img/tutorials/setup-intellij-gradle/new-project-2.png){:draggable="false"}

**11.** Click `Finish`
>![](/img/tutorials/setup-intellij-gradle/new-project-3.png){:draggable="false"}

**12.** Locate the `build.gradle` file and open it
>![](/img/tutorials/setup-intellij-gradle/after-finished.png){:draggable="false"}

**12.** Add the Javacord dependency. Your `build.gradle` file should now look like this
```groovy
plugins {
    id 'java'
}

group 'com.github.yourname'
version '1.0-SNAPSHOT'

sourceCompatibility = 1.8

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.javacord:javacord:${latest-version}'
}
```

**13.** Create a new package in the `src/main/java` folder
>![](/img/tutorials/setup-intellij-gradle/new-package.png){:draggable="false"}
>![](/img/tutorials/setup-intellij-gradle/new-package-2.png){:draggable="false"}

**14.** Create a new class inside this package
>![](/img/tutorials/setup-intellij-gradle/new-class.png){:draggable="false"}
>![](/img/tutorials/setup-intellij-gradle/new-class-2.png){:draggable="false"}

**14.** You can now start coding! Example code:
```java
package com.github.yourname;

import org.javacord.api.DiscordApi;
import org.javacord.api.DiscordApiBuilder;

public class Main {

    public static void main(String[] args) {
        // Insert your bot's token here
        String token = "your token";

        DiscordApi api = new DiscordApiBuilder().setToken(token).login().join();

        // Add a listener which answers with "Pong!" if someone writes "!ping"
        api.addMessageCreateListener(event -> {
            if (event.getMessage().getContent().equalsIgnoreCase("!ping")) {
                event.getChannel().sendMessage("Pong!");
            }
        });

        // Print the invite url of your bot
        System.out.println("You can invite the bot by using the following url: " + api.createBotInvite());
    }

}
```
## Run the code

You can run your code by clicking on the small green arrow
>![](/img/tutorials/setup-intellij-gradle/run-the-bot.png){:draggable="false"}