# Spigot Command API by Curxxed

A modern, annotation-driven command API for Spigot plugins that removes the need for implementing `CommandExecutor` for every command.

---

## 📑 Table of Contents

- [Features](#-features)
- [Why Use This?](#-why-use-this)
- [Dependency](#-dependency)
- [Example Usage](#-example-usage)

---

## ✨ Features

- No `CommandExecutor` boilerplate
- Register commands with little to no difficulty
- No `plugin.yml` command declarations
- Fully annotation-driven
- Built-in support for permissions, aliases, usage hints, and more

---

## 🧠 Why Use This?

**Traditional Spigot command handling:**
- Write a handler class for every command
- Register them manually in `plugin.yml`
- Perform permission checks and console validation yourself

**With this API:**
- Use annotations for configuration
- Register commands easily
- Skip `plugin.yml` editing altogether

---

## 📦 Dependency 

# Maven:

Add the following to your `pom.xml` to use CommandAPI as a dependency:

Repository:

```xml
<repository>
    <id>jitpack.io</id>
    <url>https://jitpack.io</url>
</repository>
```

Dependency

```xml
<dependency>
    <groupId>com.github.curxxed-mc</groupId>
    <artifactId>CommandAPI</artifactId>
     <version>1.0</version>
</dependency>

```

Gradle:

Add the following in your settings.gradle at the end of repositories:

```xml
dependencyResolutionManagement {
     repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
     repositories {
         mavenCentral()
         maven { url 'https://jitpack.io' }
   }
}
```

And then add the dependency in your buid.gradle:
```xml
dependencies {
    implementation 'com.github.curxxed-mc:CommandAPI:1.0'
}
```

For settings.gradle.kts at the end of repositories:

```xml
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        mavenCentral()
        maven { url = uri("https://jitpack.io") }
    }
}
```

build.gradle.kts:

```xml
dependencies {
    implementation("com.github.curxxed-mc:CommandAPI:1.0")
}
```

---

## 🚀 Example Usage

### 1. Create Your Command Class

```java
import net.curxxed.dev.CommandAPI.BaseCommand;
import net.curxxed.dev.CommandAPI.Command;
import net.curxxed.dev.CommandAPI.CommandArgs;
import org.bukkit.entity.Player;

public class Test extends BaseCommand {

    @Command(
        name = "test",
        permission = "ifactions.test",
        description = "Test command",
        usage = "/test",
        aliases = {"t"},
        inGameOnly = true
    )
    @Override
    public void onCommand(CommandArgs commandArgs) {
        Player p = commandArgs.getPlayer();
        p.sendMessage("This is a test to make sure the command system works!");
    }
}
```

### 2. Setup Your Plugin Main Class

Ensure your main class extends `JavaPlugin`, and define a `registerCommands()` method.

```java
@Override
public void onEnable() {
    registerCommands(); // Register commands during plugin startup
}

public void registerCommands() {
    // Initialize the command system
    new CommandManager(this);

    // Instantiate each command to auto-register it
    new Test(); // Example command class
}
```

### 3. That’s It!

No need to:
- Implement `CommandExecutor`
- Add command entries to `plugin.yml`

Everything is handled through annotations and automatic registration.


## Feel free to use this API in your projects!

### This API should work on every version of minecraft!
