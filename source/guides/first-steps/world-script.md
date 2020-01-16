Your First World Script
-----------------------

```eval_rst
.. contents:: Table of Contents
    :local:
```

### World Script Basics

A world script is a script that is automatically triggered when a given event occurs in the server. They can consist in execute a given task script with the `run` or the `inject` command or specific instructions under an event block.

Like task scripts, world scripts will run all of the Denizen commands that they include when a given event occurs on the server. World scripts are useful when you want to handle an action and determine actions in consequences. World script can listen your players when they interacts with something or help you to create visual interfaces with custom inventories.

## Wait, "an event" ?

An event is something that occurs on your server. It can be, for example, fired by an entity doing something, or a player doing something. Let's say we want to prevent players from breaking blocks. We know that there is thing to handle this : the `on player breaks block` event, so we have to monitor this event, listen if the block is an emerald ore block, and cancel the event.

### World Script Syntax

Here's an example of a basic functionnal world script.

```dscript_green
example_world_script:
    type: world
    events:
        on player breaks block:
        - narrate "You breaked a block!"
```
This script will narrate the text: `You breaked a block!` to the player attached to the event, that is to say every player that breaks a block, everywhere.

Note that this script sample is highlighted in green. That means it's good enough that you could copy/paste it and it will work, but beware, such a world script with a `on player breaks block:` event will interact with *all* your players breaking *any* blocks *everywhere*, so that can be inconfortable. Let's see of what a world script is made of and how to build it.

### Building Your World Task Script in VS Code

Previously, you've learned [how to set up VS Code](/guides/first-steps/script-editor), the editor that we recommend for writing Denizen scripts.

#### Creating the File

To create your first world script, start by opening your scripts folder in VS Code.

![](https://i.alexgoodwin.media/i/denizen_guide/548218.png)
![](https://i.alexgoodwin.media/i/denizen_guide/d2810b.png)

From there, right click the scripts folder in the explorer menu and click the "New File" option.

![](https://i.alexgoodwin.media/i/denizen_guide/5fad5b.png)

Type any file name you want, just make sure to end it with `.dsc` - the required extension for a Denizen script file.

![](https://i.alexgoodwin.media/i/denizen_guide/e3ec76.png)

Now you can begin writing your first world script!

#### Writing the Script

Let's start with the core of the script:

```dscript_blue
my_first_world_script:
    type: world
    events:
        on player places block:
        - narrate (sometext)
```

This example should look familiar - it's very similar to the example above, except we use the `on player places block` instead of `on player breaks block`.
