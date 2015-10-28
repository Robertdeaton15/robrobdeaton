```
TextBubble.cs
```

##Description
The text bubble is used for displaying simple text messages.  
It can contain any string of characters.

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Message
```c#
string bubble.Message
```
Contains the bubble's message. 

Example:
```c#
message = bubble.Message;
//status is now equal to Hello World!
```

###Emoji
```c#
List<Emoji.Span> bubble.EmojiSpans
```
???

Example:
```c#
emoji = bubble.EmojiSpans;
//status is now equal to ???
```