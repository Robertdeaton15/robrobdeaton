##Abstract
Plugin Manifests store the information associated with your plugin. Their file name has to be *PluginManifest.xml* and they have to reside in your project's assemblies directory.

##Creating the file
Right click on your plugin project in Xamarin Studio to unveil the contextual menu. Hover over 'Add' and choose 'New file...'.

On the left now choose 'XML' and name your file 'PluginManifest.xml'. Hit 'New' to finish.

![](http://i.imgur.com/XlmsE5p.png?1)

##Filling in the information
Double click on your newly created `PluginManifest.xml` to reveal its contents (It should be blank right now! :smile:)

Now use the following template to create your plugin's manifest.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<plugin>
  <name>WackyMessenger</name>
  <version>1</version>
  <minimumframeworkversion>1</minimumframeworkversion>
  <production>true</production>
  <author>John Doe</author>
  <externalmanifest>http://example.com</externalmanifest>
</plugin>
```

Now let's go through each element and explain.

`<name>` contains the plugin name that you chose when creating your plugin  
`<version>` contains the plugin version number, can be any integer  
`<minimumframeworkversion>` contains the minimum required Disa framework version that the plugin needs to run  
`<production>` is set to true if the plugin is in production mode  
`<author>` contains the plugin author's name  
`<externalmanifest>` contains the URL of an external manifest file  

Now you should be set to go ahead and deploy your plugin to your Android installation of Disa.

##Further reading

- [Deploying your plugin on Android](//github.com/Disa-im/DisaOpenSource/wiki/Deploying-on-Android)
- [The most basic plugin](//github.com/Disa-im/DisaOpenSource/wiki/The-Most-Basic-Plugin)