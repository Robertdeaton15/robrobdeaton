```
ImageBubble.cs
```

##Description
The image bubble is used for displaying image messages.  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Resource Type
```c#
Type bubble.ImageType
```
Contains the resource type of the Bubble's image.  
Can be either `Url` for a URL requested audio file, or `File` for an attached audio file

Example:
```c#
type = bubble.AudioType;
//type is now equal to Url
```

###Thumbnail Bytes
```c#
byte[] bubble.ThumbnailBytes
```
Contains the image thumbnail's bytes.

Example:
```c#
thumbnail = bubble.ThumbnailBytes;
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

###Animation
```c#
bool bubble.IsAnimated
```
Contains the information if the image is animated.

Example:
```c#
is_animated = bubble.IsAnimated;
//is_animated is now equal to false
```

###File Name
```c#
string bubble.FileName
```
The image's filename.

Example:
```c#
filename = bubble.FileName;
//filename is now equal to http://example.com/test.png
```