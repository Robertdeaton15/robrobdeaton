```
VideoBubble.cs
```

##Description
The video bubble is used for displaying video messages.  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###VideoPathNative
```c#
string bubble.VideoPathNative
```
Contains the video's path. 

Example:
```c#
path = bubble.VideoPathNative;
```

```
VideoBubble.cs
```

##Description
The image bubble is used for displaying image messages.  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Resource Type
```c#
Type bubble.VideoType
```
Contains the resource type of the Bubble's video.  
Can be either `Url` for a URL requested video file, or `File` for an attached video file

Example:
```c#
type = bubble.VideoType;
//type is now equal to Url
```

###Thumbnail Bytes
```c#
byte[] bubble.ThumbnailBytes
```
Contains the video thumbnail's bytes.

Example:
```c#
thumbnail = bubble.ThumbnailBytes;
```

###File Name
```c#
string bubble.FileName
```
The video's filename.

Example:
```c#
filename = bubble.FileName;
//filename is now equal to http://example.com/test.mp4
```