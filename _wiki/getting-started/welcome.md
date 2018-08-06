---
title: Welcome
position: 1
redirect_from: "/wiki/"
---
![](/img/javacord3_banner.png)

## Introduction

Welcome to the Javacord wiki! You can find all important topics on the right side.

## Download / Installation

The recommended way to get Javacord is to use a build manager like Gradle or Maven.  
If you are not familiar with build managers, you can follow the Setup Guide 
or download it directly from
[TeamCity](https://ci.javacord.org/viewType.html?buildTypeId=Javacord_PublishSnapshots&branch_Javacord=v_3&tab=buildTypeStatusDiv&state=successful).
Just click on the latest build and, there, go to the "Artifacts" tab to download the files.

### Javacord Dependency

#### Gradle
```groovy
repositories { mavenCentral() }
dependencies { compile 'org.javacord:javacord:${latest-version}' }
```

#### Maven
```xml
<dependency>
    <groupId>org.javacord</groupId>
    <artifactId>javacord</artifactId>
    <version>${latest-version}</version>
    <type>pom</type>
</dependency>
```

### Optional Logger Dependency

Any Log4j-2-compatible logging framework can be used to provide a more sophisticated logging experience
with being able to configure log format, log targets (console, file, database, Discord direct message, ...),
log levels per class, and much more.

For example, Log4j Core in Gradle
```groovy
dependencies { runtimeOnly 'org.apache.logging.log4j:log4j-core:2.11.0' }
```
Take a look at the [Logger Configuration](/wiki/basic-tutorials/logger-configuration/) article for further information.

## IDE Setup

If you've never used Gradle or Maven before, you should take a look at the setup tutorial:
* **[IntelliJ & Gradle](/wiki/getting-started/intellij-gradle)** _(recommended)_
* **[IntelliJ & Maven](/wiki/getting-started/intellij-maven)**
* **[Eclipse & Maven](/wiki/getting-started/eclipse-maven)**

## Examples

There's an example bot written with Javacord: [Javacord Example Bot](https://github.com/Javacord/JavacordExampleBot)
