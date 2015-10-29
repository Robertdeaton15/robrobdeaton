This reference page contains all commands currently working in Disa.Terminal.

##Commands
`startall`  
This command starts all registered services.

`start [ServiceName]`  
This command starts the stated plugin.

`stop [ServiceName]`  
This command stops the stated plugin.

***

`send [ServiceName] [Addressee] [Message]`  
This command sends a [Text Bubble](//github.com/Disa-im/DisaOpenSource/wiki/Bubble-Type:-Text-Bubble) to the stated addressee using the stated service.

***

`deploy-register [ServiceName] [PathOfAssemblies]`  
This command registers a plugin for deployment. [Learn more](//github.com/Disa-im/DisaOpenSource/wiki/Deploying-on-Android#registering-your-plugin-for-deployment)

`deploy-unregister [ServiceName]`  
This command removes the registration of a plugin to start over again with `deploy-register`.

`deploy [ServiceName]`  
This command deploys the stated plugin to your Disa Android installation. [Learn more](//github.com/Disa-im/DisaOpenSource/wiki/Deploying-on-Android)

`deploy-dependencies [ServiceName]`  
*Incomplete* Check out Program.cs if you really need to know.