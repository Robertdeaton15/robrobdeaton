```
StickerBubble.cs
```

##Description
The sticker bubble is used for displaying sticker messages (e.g. stickers on Facebook).  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Resource Type
```c#
Type bubble.AudioType
```
Contains the resource type of the Bubble's audio.  
Can be either `Url` for a URL requested image file, or `File` for an attached image file

Example:
```c#
type = bubble.StickerType;
//type is now equal to Url
```

###Height
```c#
int bubble.Height
```
Contains the height of the bubbles sticker image in pixels.

Example:
```c#
height = bubble.Height;
//height is now equal to 100
```

###Width
```c#
int bubble.Width
```
Contains the width of the bubbles sticker image in pixels.

Example:
```c#
width = bubble.Width;
//width is now equal to 100
```

###Download Attempts
```c#
int bubble.DownloadAttempt
```
How many times the bubble has attempted to download the file. 

Example:
```c#
attempts = bubble.DownloadAttempt;
//attempts is now equal to 3
```

###Sticker ID
```c#
string bubble.StickerId
```
The sticker's id.

Example:
```c#
id = bubble.StickerId;
//id is now equal to happy
```

###File Name of Static Image
```c#
string bubble.StaticImage
```
The stickers static image path.

Example:
```c#
static = bubble.StaticImage;
//static is now equal to http://example.com/test.png
```

###File Name of Animated Image
```c#
string bubble.AnimatedImage
```
The stickers animated image path.

Example:
```c#
animated = bubble.AnimatedImage;
//animated is now equal to http://example.com/test.png
```