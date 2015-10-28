This reference page contains all properties that can be read from a Bubble object.

##Status
```c#
BubbleStatus bubble.Status
```
Is equal to `Sent` if the bubble was sent correctly.  
Is equal to `Delivered` if the bubble was delivered.  
Is equal to `Waiting` if the bubble is waiting to be sent.  
Is equal to `Failed` if sending the bubble failed.   

Example:
```c#
status = bubble.Status;
//status is now equal to Sent
```

##Message
```c#
string bubble.Message
```
Contains the message of the bubble.

Example:
```c#
message = bubble.Message;
//direction is now equal to Hello World!
```

##Time
```c#
long bubble.Time
```
Contains the timestamp at which the bubble was created in the Epoch/Unix-Timestamp format.

Example:
```c#
timestamp = bubble.Time;
//timestamp is now equal to 1446035271
```

##Direction
```c#
BubbleDirection bubble.Direction
```
Contains the direction which the bubble is in. Possible values are:  
`Incoming` for incoming bubbles, `Outgoing` for outgoing bubbles

Example:
```c#
direction = bubble.Direction;
//direction is now equal to Incoming
```

##Address
```c#
string bubble.Address
```
Contains the address of the bubble.

Example:
```c#
address = bubble.Address;
//address is now equal to 12345
```

##Participant Address
```c#
string bubble.ParticipantAddress
```
Contains the address of the bubble participant.

Example:
```c#
paddress = bubble.ParticipantAddress;
//paddress is now equal to 67890
```

##Party
```c#
bool bubble.Party
```
Contains information if the bubble is part of a party or not.

Example:
```c#
is_party = bubble.Party;
//is_party is now equal to false
```

##Service
```c#
Service bubble.Service
```
Contains the service which the bubble was sent with.

Example:
```c#
service = bubble.Service;
//service is now equal to Disa.Framework.WackyMessenger.WackyMessenger
```