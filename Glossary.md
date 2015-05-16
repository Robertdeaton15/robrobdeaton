### Plugins & Services

At the moment, these are really used interchangeably. A plugin implies a service, and a service implies a plugin. However, as Disa expands, and we allow plugins to be more than services (think big picture), this implication will probably be broken. That is, a plugin won't imply just a service - it will be multi-faceted. 

### Bubble

A bubble can either be a visual message (image, video, audio, file, text, etc.) or an abstract message (like whether or not a conversation was read or not - a ReadBubble).

The concept of a bubble is essentially the core idea in Disa. The framework and services (plugins) constantly catapult bubbles back and forth to/from each other. These bubbles literally end up making everything happen. Where there's more information needed about a collection of bubbles (e.g: what are they all collectively called?!), a BubbleGroup is defined.

### BubbleGroup

A bubble group is a collection of bubbles. A bubble group can also have a name, image thumbnail, presence, last seen time, etc. associated with it. To see the full list, please visit BubbleGroup.cs in the Disa.Framework folder.

In other words, BubbleGroup is really just a different name to a 'thread' or a 'conversation'. A BubbleGroup of 10 bubbles, with the name of "Meghan Smith", a thumbnail of her face... yeah, you get the idea.

