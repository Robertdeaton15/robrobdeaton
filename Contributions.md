There's a lot of work to be done on the Framework. Also, building new front-ends will diversify the platforms Disa runs on.

Here's a quick breakdown of what can be done:

* Documentation - We need a lot of help in this category. 
    1. If you're really good at formatting markdown or making edits to to any of the Wiki contents, you are more than welcome to do so.
    2. If you'd like to make more tutorials, add glossaries, etc. (really anything Wiki related), you are more than welcome.
    3. Documentation in code is also a must! If you'd like to work on this, you're also more than welcome!

* Build multiple GUI Front-Ends (one for Mac, Windows, Linux, iOS, Windows Phone, etc.) Mono/.NET has really good support for multiple platform tools. Xamarin.Mac/MonoMac will be a good candidate for Mac, Windows has WPF/WinForms, iOS has Xamarin.iOS, and Linux has GTK#. XWT (https://github.com/mono/xwt) also provides a fantastic cross-platform approach for the smaller bits of UI that look fairly similar across all platforms.

* Make Disa.Terminal really awesome and feature rich.
    1. Finish WindowsUnix.cs.
    2. Expand the commands to cover the entire framework (this is being done as the tutorials are being published).

* When Disa initializes, the last bubble from each BubbleGroup file is loaded in to populate the conversation list. On large conversation lists (100+) init becomes pretty slow.
    * To improve this, a table should be kept updated. When Disa is first initialized, this table is then read from. This will significantly improve startup performance of large conversation lists. If you are interested in working on this, send us an email at opensource@disa.im

* Introduce typing bubbles for parties.

* Disa plugins cannot yet use referenced PCLs. Currently, all assemblies must be compiled with the Mono / .NET 4.5 target framework. To make this possible, you will need to use Mono.Cecil to remap all System.* reference libraries to their .Net 4.5 counterpart. For instance, "System.Linq.dll" will be remapped to "System.Core.dll". Changing an assemblies mapping is easy (with Cecil: iterating through a module's AssemblyReferences, and change each one's Name to the .Net 4.5 counterpart) - one just needs to build a mapping.
    * Unfortunately, it's not this simple in some cases. Some Types in one PCL namespace will be in multiple .Net 4.5 assemblies (e.g: try mapping System.Collections.Concurrent.dll). Thus, one will have to find these exceptions and fix the type's scopes which reference them. This should be fairly easy to accomplish with Mono.Cecil.


* More to come.