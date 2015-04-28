## Abstract

If you ventured into here by now, you're probably wanting to know how to start building a plugin.

This tutorial will guide you into building a very basic plugin for WackyMessenger (a made-up service). WackyMessenger is incredibly basic - it only supports text messages. When a user sends a text message, it waits a few seconds, and then responds to the user with his or her message reversed.

You'll first be using the Disa.Terminal front-end for quick deployment and debugging. Then, once we are satisfied with WackyMessenger, you'll be deploying it to the Disa Android application found on the Play Store.

The source to this plugin can be found in full under the Examples folder in the main directory.

## Definitions Before We Begin

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

* We will be using event driven bubbles. What does this mean? Some services require a dedicated thread to be infinitely polling against a keep-alive connection. By setting event driven bubbles to false, the ProcessBubbles iterator block is called in an infinite threaded loop while the service is running. Thus, the Framework completely manages this aspect of keeping the _poller_ constantly alive. By settings event driven bubbles to true, you are effectively telling the Framework: "I want to manage all the polling myself, and invoke off the EventBubble method whenever I a new bubble comes in."
* We will not be using media progress. We don't support anything but text bubbles. If your service can support giving feedback back to the client on the upload process of media bubbles (images, videos, etc), you'll set this flag to true and then use the Transfer.Progress callback in the associated media bubble you're uploading.
* This service does not use internet. If it we set this to true, then the Framework will ensure that the service is stopped if there is no internet connection.
* This service does not support battery savings mode.
* This service does not use delayed notifications. Delayed notifications will delay notification dispatches by 1 (one) second. Setting this to true and using NotificationManager.Remove allows you to have multiple clients working together without notifications going off while chatting on another client.
* The Framework manages a settings store of your service. You can use this to store any information. WackyMessenger doesn't need to store anything, so we don't need it. Additionally, you can use MutableSettings and MutableSettingsManager to save information you find yourself frequently saving (such as a timestamp you need to keep updated everytime the service is started).
* The procedure type is set to ConnectAuthenticate. This means that the service scheduler will call Connect before calling Authenticate. The other option is AuthenticateConnect - which called Authenticate before Connect. Once again, the option is given here because some services require Authenticating before connecting, and vice-versa. 

It also should be mentioned that if you use files, audio, or video bubbles in your plugin, you need to add the associated attribute. These can be found in ServiceInfo.cs.

Great! Now let's talk a bit about the starting of your newly implemented service.

## Service Start Process

The first thing that happens is that InitializeDefault() is called. It attempts to try and start the service without any settings. If this method returns true, it is assumed your service doesn't need any settings. Authenticate and Connect is then directly called afterwards (the order of which one is first depends on your set procedure type, as mentioned above). If this method returns false, then InitializeDefault(DisaSettings) is called - the framework provided you with your stored settings. Whenever you want to save your settings, you can call SettingsManager.Save.

So, for WackyMessenger, all we need to do is initialize the default - we are not using Settings.

```c#
public override bool InitializeDefault()
{
     return true;
}
```

For connect, WackyMessenger doesn't really connect to anything. So, we can just leave it blank:
```c#
public override void Connect(WakeLock wakeLock)
{
   // do nothing
}
```

As with Authenticate:
```c#
public override bool Authenticate(WakeLock wakeLock)
{
   return true;
}
```

What exactly is that WakeLock? Whenever Disa executes one of these methods, it holds a wake lock on the method's duration so the phone doesn't fall asleep and stop your service's starting process. However, wake locks are expensive to battery life. If you know that you can temporarily free the wakelock (such as when you're awaiting for a response from a server), you can use WakeLock.TemporaryFree disposable (wrap it in a using statement) to do so). Battery life is important, and this a well tuned plugin can save good battery life.

> Aside: Whenever you are awaiting data from a socket connection (including HTTP connections) in Android, you can allow the device to fall asleep. When there's a response from the socket, your device will be woken back up, allowing the newly presented data to be processed. This is the motivation behind the temporary free optimization.

In the event that Authenticate or Connect doesn't succeed, and can just pass up the exception to the Framework. It will deal with a connection failure or authentication failure accordingly. However, there are some exceptions to let the Framework know that there is something particularly wrong. For example, passing a ServiceExpiredException in one of these methods will let the Framework know that the service has expired (subscription needs to be repaid for example). For more exceptions, take a look at all the defined *Exceptions in the framework, and their mappings into the service scheduler.

# Service Stop Process

When a service is stopped, two methods are called: Deauthenticate and Disconnect. The order once again depends on the procedure type. Use these methods to teardown your service.

In WackyMessenger, we can simply ignore them, as there's nothing to teardown:
```c#
public override void Deauthenticate()
{
    // do nothing
}

public override void Disconnect()
{
    // do nothing
}
```

## Interim Summary

Your code should now look like this:

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
            return true;
        }

        public override bool Authenticate(WakeLock wakeLock)
        {
            return true;
        }

        public override void Deauthenticate()
        {
            // do nothing
        }

        public override void Connect(WakeLock wakeLock)
        {
            // do nothing
        }

        public override void Disconnect()
        {
            // do nothing
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

## Implementing bubble sending

Great. So now, the service will both start and stop. Its pretty damn useless though. Lets add some sending:











