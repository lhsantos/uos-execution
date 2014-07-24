Execution Driver
================

This Project is part of the uOS:http://ubiquitos.googlecode.com middleware project.
It provides ways to explore the CPU of a device as a open resource.
For such any application on the Smart Space can send pieces of code that
wants to be executed remotely.
The purpose of this project is to provide methods for:

* Remote Execution using Lua Scripts
* Agent Execution using Java Agents
* Driver and Application Downloads using OSGi bundles

The driver name is *"uos.ExecutionDriver"*

remoteExecution:
----------------
	
To use the remote execution service just call the service named *"remoteExecution"*.

*Parameters:*

* *"code"*: Lua code that is going to be executed.
 * Any other parameter will informed will be available to the script during execution.

In the lua script two methods provides a way to interact with the service call:

* *get(_key_)*: provide a way to access the parameters informed during the call.
* *set(_key, value_)*: set the values that will be returned after execution is finished.
	
executeAgent:
-----------------

To use the agent service just call the service named *"executeAgent"*.
Two types of agents are accepted:

* Explicit agents implements the *org.unbiquitous.driver.execution.executeAgent.Agent* interface and have full access to the Smart Space through the *Gateway* object.
* Implicit agents implements only a run(Map) method and has limited access to the Smart Space using the informed map.

To move an agent the best way is to use the AgentUtil methods.

Ex:
```Java
	AgentUtil.move(new MyAgent(),targetDevice,gateway);
```
	
If you want to call the service directly, keep in mind that itd demands a code stream to be trasmited. This stream contains the jar of the transmited code.
