## Abstract

**This page is still in need of a lot of formatting and picture-adding. Please help out!**

Disa.Terminal ships with the ability to automatically deploy your plugin to Disa.

## PCL Limitations
At this point of time, unfortunately Disa.Android does not support PCL work. If you'll like to make that possible, check out the Contributions page.

## Working Around Nuget Packages
* If you're referencing Nugets in your project, open the directory where these Nugets are installed (typically a folder named 'packages' in your solutions root directory). Then, open them, and follow-through to the net45 directory. Copy the DLLs presented in there, and add them as a manual reference to your project. Finally, ensure that you delete the Nuget package reference.

**OR**

* Open the references from your Nuget packages in your IDE, effectively opening Assembly Browser. Look for the TargetFramework, it should be something along the lines of ".NETFramework,Version=v4.5". If it has the substring "PCL" in it, you'll need to use the aforementioned process. Do these for all of the PCL references.

## An Icon Is Required
Before deploying to Android, it's necessary to include an icon in your plugin. Please visit [Creating a Plugin Icon](https://github.com/Disa-im/DisaOpenSource/wiki/Creating-A-Plugin-Icon) for more information.

##Registering Your Plugin For Deployment
To register the Android deployment, fire up Disa.Terminal, and type:

`deploy-register [PluginName] [PathOfAssemblies]`

_PluginName_ is your plugin name (e.g: Telegram). And, _PathOfAssemblies_ is where all the assemblies generated for your plugin are located (e.g: the debug/release output folder of your plugin's project). 
The supplied path should be the full path e.g. */Users/username/Downloads/DisaOpenSource-master/Disa.Framework.WackyMessenger/*.

Please note that Disa.Terminal will filter out all of the assemblies that it doesn't need to package (i.e: the ones that ship with the Disa.Android build).

##Deploying Your Plugin
**Make sure the Disa Android app is set to Use Public Storage.**

You will need a PluginManifest.xml file. This manifest file needs to be in the same directory as your assemblies are (i.e: _PathOfAssemblies_). To set one up, check out this tutorial: [Creating the Plugin Manifest](//github.com/Disa-im/DisaOpenSource/wiki/Creating-the-Plugin-Manifest)

To deploy the plugin, type:

`deploy [PluginName]`

The plugin will now be deployed to Disa! Disa will automatically restart, and load in your plugin!

## My Plugin Doesn't Work
If your plugin does not work (which will probably crash the app), be sure to check out your device's logcat. In most cases, it is because you have referenced a PCL library. If that's no the case, logcat will give you insights on which Types failed to be loaded in (TypeLoadException). Ensure that Logging is enabled inside the Disa application.

## FAQ
__My Disa app is bricked on my Android device. Help!__

Plugins are copied to /sdcard/disa/plugins/ on your Android device. If everything hits the fan and you brick your Disa Android install, just delete the associated folder in that directory (its your plugin name). You'll be up and running again!
















