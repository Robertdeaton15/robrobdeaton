```
AudioBubble.cs
```

##Description
The text bubble is used for displaying voice messages or other audio files.  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Resource Type
```c#
Type bubble.AudioType
```
Contains the resource type of the Bubble's audio.  
Can be either `Url` for a URL requested audio file, or `File` for an attached audio file

Example:
```c#
type = bubble.AudioType;
//type is now equal to Url
```

###Recording
```c#
bool bubble.Recording
```
If the Audio Bubble is recording or not.

Example:
```c#
recording = bubble.EmojiSpans;
//recording is now equal to true
```

###Length
```c#
int bubble.Seconds
```
Contains the length of the bubbles audio in seconds.

Example:
```c#
length = bubble.Seconds;
//length is now equal to 10
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

###File Name
```c#
string bubble.FileName
```
The audios filename.

Example:
```c#
filename = bubble.FileName;
//filename is now equal to http://example.com/test.wav
```