There's a lot of work to be done on the Framework. Also, building new front-ends will diversify the platforms Disa runs on.

Here's a quick breakdown of what can be done:

* Build multiple GUI Front-Ends (one for Mac, Windows, Linux, iOS, Windows Phone, etc.) Mono/.NET has really good support for multiple platform tools. Xamarin.Mac/MonoMac will be a good candidate for Mac, Windows has WPF/WinForms, iOS has Xamarin.iOS, and Linux has GTK#. XWT (https://github.com/mono/xwt) also provides a fantastic cross-platform approach for the smaller bits of UI that look fairly similar across all platforms.

* Make Disa.Terminal really awesome and feature rich.
    1. Finish WindowsUnix.cs.
    2. Expand the commands to cover the entire framework (this is being done as the tutorials are being published).

* When Disa initializes, the last bubble from each BubbleGroup file is loaded in to populate the conversation list. On large conversation lists (100+) init becomes pretty slow.
    * To improve this, a table should be kept updated. When Disa is first initialized, this table is then read from. This will significantly improve startup performance of large conversation lists. If you are interested in working on this, send us an email at opensource@disa.im

* Introduce typing bubbles for parties.

* More to come...