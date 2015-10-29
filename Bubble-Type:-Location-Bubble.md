```
LocationBubble.cs
```

##Description
The location bubble is used for displaying a location on a map.  

##Special Properties
> The following properties are special to this bubble type. In addition, there are bubble properties which apply to all bubble types. [Those are listed here.](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Properties)

###Latitude
```c#
double bubble.Latitude
```
Contains the latitude of the location to show.

Example:
```c#
lati = bubble.Latitude;
```

###Longitude
```c#
double bubble.Longitude
```
Contains the width of the bubbles sticker image in pixels.

Example:
```c#
long = bubble.Longitude;
```

###Name
```c#
string bubble.Name
```
The location's name.

Example:
```c#
id = bubble.Name;
//id is now equal to Berlin
```

###Thumbnail
```c#
byte[] bubble.Thumbnail
```
The stickers static image path.

Example:
```c#
thumbnail = bubble.Thumbnail;
//thumbnail is now equal to the map's thumbnail
```