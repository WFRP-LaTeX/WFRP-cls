# WFRPTeX

## Description

This package provides a new LaTeX class useful for creating fan-made WFRP content.
It provides some useful environments and commands for formatting stat blocks,
and sets fonts, page margins, etc. for easy reading.

## Copyright and license

Copyright (c) 2018 Ian Knight.

## Installation

Either clone this repository, or copy the ``.cls`` file, into your TeX root. On my
machine, that's ``/home/me/texmf/tex/latex``.

## Usage

To make use of the class, use ``\documentclass{wfrp}`` at the top of your main
file. Currently, the ``wfrp`` class has no options.

### Player callouts

Often, it is useful to mark a paragraph as intended for reading out to the players
(e.g., descriptions of important NPCs). To make these, simply use the ``callout``
environment. By default, the callout will be shaded light grey, and the text will be
made italic.

    \begin{callout}
    This paragraph is meant to be read out to players, as description.
    \end{callout}

### Notes for the GM

In places, it may be helpful to add extra notes for the GM describing optional
changes they might like to make to an adventure, such as contingencies for if players
make ridiculous choices and kill the antagonist before the adventure's even begun.
To mark these out, use the ``gmnote`` environment. This environment is a float.

    \begin{gmnote}
    In case the players have already killed Graf Sebastian, go straight to the
    conclusion of the adventure.
    \end{gmnote}

### Stat blocks
The key feature of the class
is a series of ``\statblock`` commands that take varying numbers of arguments. These are
detailed below:

 * ``\statblock``

   This command creates a simple stat block similar to those presented in the Bestiary.
   It takes three arguments: the name of the creature/NPC in the stat block, its
   stats including Movement and Wounds, formatted like a tabular row, and a list of
   creature abilities. Example:

       \statblock{Street Thug}
           {4 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 12}
           {Armour +1, Weapon +7}

 * ``\statblockfull``

   This is similar to ``\statblock``, but is designed to provide a fuller stat block
   suitable for key NPCs. It takes five arguments: name, stats, skills, talents, and
   trappings.

       \statblockfull{Street Thug}
           {4 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 12}
           {Melee (Brawling) +5, Cool +5, Dodge +5}
           {Street Fighting}
           {Knuckledusters, Club, Bottle of ale}

 * ``\statblockmagic`` and ``\statblockfullmagic``

   These two commands extend the basic ``\statblock`` and ``\statblockfull`` by accepting
   an extra argument providing a list of spells known to the character. For the short stat
   block, the extra argument is given at the end; for the full block, the argument comes
   just before the character's trappings.

       \statblockfullmagic{Street Wizard}
           {4 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 12}
           {Melee (Brawling) +5, Cool +5, Dodge +5, Channelling (Aqshy) +5, Language (Magick) +5}
           {Street Fighting, Petty Magic}
           {Dart}
           {Knuckledusters, Club, Bottle of ale}

 * ``\statblockreligious`` and ``\statblockfullreligious``

   These two commands are similar to the previous two, except that they allow for specifying
   Blessings and Miracles known to the character, instead of Spells. They provide two extra
   arguments compared to their base forms, given in the same order as for the magic stat blocks.

       \statblockfullreligious{Street Preacher}
           {4 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 30 & 12}
           {Melee (Brawling) +5, Cool +5, Dodge +5, Pray +5}
           {Street Fighting, Bless (Ranald)}
           {Protection}
           {\textit{None}}
           {Knuckledusters, Club, Bottle of ale}
