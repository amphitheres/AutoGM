# Data structure

How we plan on storing the data for the game. Since we already agreed it will be multiple files, we should establish the
following so we know how to do the data processing:

* What should a file contain? Should it contains Nouns, like places, creatures, or players?
* At what size should we limit the files? What is the optimal amount of config per file.
* How should we separate modifiers and items (do they work differently on different monsters/players e.c.t.)?
* How will we store specific actions inside of memory? Will the entire YAML be loaded into RAM?
* How will the bot know how to load the configuration and files for a specific game? (will it be dir based?)

# Flynn Proposal:

Common classes will be defined inside of the code itself, that are commonly found in RPG games.
`Monster`, `Player`, `Item`, `Location` should be instances we can define.

The properties of each instance (i.e. new Monster generated, should be defined in the main game config file `something.yaml`)
Then, when the game initializes, the basics will be initalised. I am guessing that the bot will be a selection based game,
with a numbering based sleection that is user specific (only accepts commands from the user who currently has a turn).

An example of an config imo (I don't actually know YAML so bear with me):
```
- Items
    - Potion
        -Modifiers
            -Health: 40
        - Cost
            -Gold: 30
            -Soul: 100
    - Max Potion
        -Modifiers
            -Helth: 80
        -Cost
            -Gold: 70
            -Soul: IDGAF
```
```
- Mosters
    - Demon
        -Attacks
            -Normal: 80
            -Hyper: 1000000000000000000000
        - Abilities:
            - BUTTER_THROW
            - EATS_ITALIAN_PEOPLE
    - Duck
        -Attacks
            -Normal: Infinity
            -Hyper: Infinity++
        - Abilities:
            - BUTTER_THROW
            - EATS_ITALIAN_PEOPLE 
            - GOD_MODE_ENABLED
```

Attacks and such are decided should be game logic based. Whether or not this is it's own config, I'm not sure. What matters
is that the monsters should have basic attacks. Perhaps an `attack.yaml` that stores common attacks types for that game
might help. For example a Poke game where the moves and abilities are common.

* * *

# Tom's proposal