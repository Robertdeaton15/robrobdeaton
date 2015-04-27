## Abstract

If you ventured into here by now, you're probably wanting to know how to start building a plugin.

This tutorial will guide you into building a very basic plugin for WackyMessenger (a made-up service). WackyMessenger is incredibly basic - it only supports text messages. When a user sends a text message, it waits a few seconds, and then responds to the user with his or her message reversed.

You'll first be using the Disa.Terminal front-end for quick deployment and debugging. Then, once we are satisfied with WackyMessenger, you'll be deploying it to the Disa Android application found on the Play Store.

The source to this plugin can be found in full under the Examples folder in the main directory.

## Setting Up Your IDE

Alright, to begin! You need to setup your IDE. We'll be using Xamarin Studio (as I am on a Mac). However, Visual Studio works just fine too and you should be able to follow along easily. If not, send us an email at opensource@disa.im and we'll figure it out.

First, clone or download this repo. Then, open it. You should be presented with a screen similar to this:

![](http://i.imgur.com/cjidLi9.png)

Now, lets add our WackyMessenger project. Add a new project, and call it Disa.Framework.WackyMessenger.

> Aside: for plugins to properly work, they need to be labelled with the Disa.Framework prefix. If for example, I was writing a Telegram plugin, I'd label the plugin project Disa.Framework.Telegram.

There will now be three projects in your solution:

![](http://i.imgur.com/QvYXp6V.png)









