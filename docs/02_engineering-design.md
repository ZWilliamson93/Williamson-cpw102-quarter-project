# Engineering Design Document


## Overview

[Provide a system-level explanation of:

- major components of your application and how they interact.
It uses room for objects for map, items and bag for players inventory.
- data flow at a high level
The game sets up room, prints starting location and waits for user commands

A friend should be able to read this section and, at a glance, understand how the application works. ]

## System Diagrams

[This document must include one or more of the following:

- block diagram of your proposed functions and modules, including external libraries

user terminal-------adventurelib engine start-----command functions-----rooms,items and inventory

- flowchart of logic for critical flows

                                               -valid command----update room/items---win or quite game?---no--loop back--yes---end
start game-----show room----wait for input-----
                                               -invalid command---print error

- mockups of any program-driven user interfaces, if applicable]

## Technical Details


### Inputs

[What information will you take from the user? How will you take it (terminal, UI, file, ext)? What data types will you need to store user-entered information? ]

What information I will take from the player is text commands(like north,take and inventory) directly in terminal.
Data type that will need to be stored are room,item and bag.

#### Handling bad inputs

[How will your app handle bad user inputs?] 
Unknown inputs will not be reqonized. then print need valid input.

### Logic

[At a high level, describe the logic you will need to apply. What Python tools will you use to capture that logic? For loops, while loops, exceptions?]
while loop to keep asking for commands. If/else statment for trigging certain actions available. for loops for bag collection

### Functions

[How will you break your flow of logic up into functions? Write some psuedo code for your `main()` function to show how your app will coordinate its duties.]

``` python
def main():
    """
    function calls go below here
    """
    pass

main()
```
from adventurelib import *

def setup_world():
    # Create rooms, connect exits, and place items
    pass

@when('look')
def look():
    # Print current room description and items
    pass

@when('north', direction='north')
@when('south', direction='south')
def go(direction):
    # Move player to new room if exit exists
    pass

@when('take ITEM')
def take(item):
    # Move item from room to player inventory
    pass

def main():
    setup_world()
    look()
    start() # Starts the adventurelib game loop

main()


This is a example but wont use exact way. I will just import from adventurelib import Room, Item, Bag, start, say.
### Libraries

[How can you leverage external libraries to:

- take advantage of functionality already written and tested by others?
- improve the performance, user experience, or features in your application?

All apps should leverage libraries. ]

The adventurelib will handle heavy lifing like commands,room connections and inventory tracking.


### Output

[What exactly will you output to the user? Options could be:

- printing a report to the terminal at the end of a program
- repeatedly giving users updates on an iterative process
- creating a file based on user-entered data

If applicable, show an example output below:]

```

A example would be:
You are in a dark hallway. A door leads north.
Items here: silver key

> take silver key
You picked up the silver key.

> north
You unlock the door and enter the treasure room. You win!