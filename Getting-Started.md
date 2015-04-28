## Abstract

If you ventured into here by now, you're probably wanting to know how to start building a plugin.

This tutorial will guide you into building a very basic plugin for WackyMessenger (a made-up service). WackyMessenger is incredibly basic - it only supports text messages. When a user sends a text message, it waits a few seconds, and then responds to the user with his or her message reversed.

You'll first be using the Disa.Terminal front-end for quick deployment and debugging. Then, once we are satisfied with WackyMessenger, you'll be deploying it to the Disa Android application found on the Play Store.

The source to this plugin can be found in full under the Examples folder in the main directory.

## Setting Up Your IDE

Alright, to begin! You need to setup your IDE. We'll be using Xamarin Studio (as I am on a Mac). However, Visual Studio works just fine too and you should be able to follow along easily. If not, send us an email at opensource@disa.im and we'll figure it out.

First, clone or download this repo. Then, open it. You should be presented with a screen similar to this:

![](http://i.imgur.com/cjidLi9.png)

Now, lets add our WackyMessenger project. Add a new Library project (not the PCL one!), and call it Disa.Framework.WackyMessenger.

> Aside: for plugins to properly work, they need to be labelled with the Disa.Framework prefix. If for example, I was writing a Telegram plugin, I'd label the plugin project Disa.Framework.Telegram.

There will now be three projects in your solution:

![](http://i.imgur.com/QvYXp6V.png)

Go ahead, and add Disa.Framework as a reference to Disa.Framework.WackyMessenger. Then, add Disa.Framework.WackyMessenger as a reference to Disa.Terminal. You'll now be left with the following:

![](http://i.imgur.com/6vrElWR.png)

Wonderful! Now we're ready to add the service skeleton.

## Add the Service Skeleton

Create a new file in Disa.Framework.WackyMessenger, calling it WackyMessenger.cs.

Paste the following into the file:

```c#
using System;
using System.Threading.Tasks;
using System.Collections.Generic;
using Disa.Framework.Bubbles;

namespace Disa.Framework.WackyMessenger
{
    [ServiceInfo("WackyMessenger", true, false, false, false, false, typeof(WackyMessengerSettings), 
        ServiceInfo.ProcedureType.ConnectAuthenticate)]
    public class WackyMessenger : Service
    {
        public override bool Initialize(DisaSettings settings)
        {
            throw new NotImplementedException();
        }

        public override bool InitializeDefault()
        {
            throw new NotImplementedException();
        }

        public override bool Authenticate(WakeLock wakeLock)
        {
            throw new NotImplementedException();
        }

        public override void Deauthenticate()
        {
            throw new NotImplementedException();
        }

        public override void Connect(WakeLock wakeLock)
        {
            throw new NotImplementedException();
        }

        public override void Disconnect()
        {
            throw new NotImplementedException();
        }

        public override string GetIcon(bool large)
        {
            throw new NotImplementedException();
        }

        public override IEnumerable<Bubble> ProcessBubbles()
        {
            throw new NotImplementedException();
        }

        public override void SendBubble(Bubble b)
        {
            throw new NotImplementedException();
        }

        public override bool BubbleGroupComparer(string first, string second)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupLegibleId(BubbleGroup group, Action<string> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupName(BubbleGroup group, Action<string> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupPhoto(BubbleGroup group, Action<DisaThumbnail> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupPartyParticipants(BubbleGroup group, Action<DisaParticipant[]> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupUnknownPartyParticipant(BubbleGroup group, string unknownPartyParticipant, Action<DisaParticipant> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupPartyParticipantPhoto(DisaParticipant participant, Action<DisaThumbnail> result)
        {
            throw new NotImplementedException();
        }

        public override Task GetBubbleGroupLastOnline(BubbleGroup group, Action<long> result)
        {
            throw new NotImplementedException();
        }
    }

    public class WackyMessengerSettings : DisaSettings
    {
        // store settings in here:
        // e.g: public string Username { get; set; }
    }
}
```

At the very top of the Service class, we specify its information (i.e: how the framework must manage it).

```c#
[ServiceInfo("WackyMessenger", true, false, false, false, false, typeof(WackyMessengerSettings), ServiceInfo.ProcedureType.ConnectAuthenticate)]
```

Some vocabulary:

1. Bubble: A message


* We will be using event driven bubbles. What does this mean? Some services require a dedicated thread to be infinitely polling against a keep-alive connection. By setting event driven bubbles to false, the ProcessBubbles iterator block is called in an infinite threaded loop while the service is running. Thus, the Framework completely manages this aspect of keeping the _poller_ constantly alive. By settings event driven bubbles to true, you are effectively telling the Framework: "I want to manage all the polling myself, and invoke off the EventBubble method whenever I a new bubble comes in."
* We will not be using media progress. We don't support anything but text bubbles. If your service can support giving feedback back to the client on the upload process of media bubbles (images, videos, etc), you'll set this flag to true and then use the Transfer.Progress callback in the associated media bubble you're uploading.
* This service does not use internet. If it we set this to true, then the Framework will ensure that the service is stopped if there is no internet connection.
* This service does not support battery savings mode.
* This service does not use delayed notifications. Delayed notifications will delay notification dispatches by 1 (one) second. Setting this to true and using NotificationManager.Remove allows you to have multiple clients working together without notifications going off while chatting on another client.
* The Framework manages a settings store of your service. You can use this to store any information. WackyMessenger doesn't need to store anything, so we don't need it. Additionally, you can use MutableSettings and MutableSettingsManager to save information you find yourself frequently saving (such as a timestamp you need to keep updated everytime the service is started).






