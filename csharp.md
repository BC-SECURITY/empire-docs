# C\#

Empire 4 combines the power of [Covenant ](https://github.com/cobbr/Covenant)and [Sharpire](https://github.com/0xbadjuju/Sharpire) to give us C# agents. In order to be able to run the C# plugin and Covenant compiler, you need to have the dotnet 3.1 SDK installed on your computer. You can follow the [Microsoft Documentation](https://docs.microsoft.com/en-us/dotnet/core/install/linux-debian#supported-distributions) or run the[ install script.](csharp.md#quickstart) When prompted for dotnet, type `y`.

As of Empire 4.3, the dotnet SDK is installed by default with the install script and the csharpserver plugin is automatically started up.

## Quickstart

Currently, the C# functionality is contained in a plugin. The plugin **MUST** be running to generate the stager and execute C# tasks. To start the server:

```
useplugin csharpserver
set status start
execute
```

![Starting C# Plugin](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_plugin.png?resize=788%2C269\&ssl=1)

To get a stager for a C# agent:

```
usestager windows/csharp_exe
set Listener <listener_name>
generate
```

Drop the stager on your windows box and execute it. You should see a callback just like any other Empire stager. Covenant modules have also been loaded into Empire. They can be executed both against the C# agent and the PowerShell agent. You can find them prefixed with `csharp/`.

![C# module execution](https://user-images.githubusercontent.com/9831420/115481326-3d2da280-a201-11eb-90d3-e00595d76c0a.png)

We found that not every engagement requires the use of installing dotnet. Since it takes up a non-trivial amount of space, we decided that we would make installing dotnet and using the C# functionality in Empire optional, at least for the moment. At some point, we may integrate the C# server directly into the Empire codebase, but for now, it is contained in a plugin. When you first boot up the C# server, it will generate the backend compiler.

## Shared Code Components (Covenant Roslyn Compiler)

When deciding to add in C# capability, we wanted to support in-place compilation instead of requiring a user to launch a secondary program and open an outputted project file to be able to use the resources. This process is tedious and not really workable for an engagement. Instead, we wanted to implement something like Covenant. After some work, we realized that instead of having something LIKE the Covenant Roslyn Compiler, we could just use the Covenant compiler.

This saved us a lot of work but, more importantly, enabled us to further our goal of making Empire interoperable with as many open source projects as possible. We think that making projects interoperable encourages more community contributions, makes upgrades easier and provides more flexibility for operators to move between projects as engagements require without having to relearn entire new codebases and project nuances. So with the integration of the Covenant Roslyn Compiler, Empire now supports the use of Covenant Task files. These tasks can be used with BOTH the C# agent and PowerShell agents. Now we will explore all the features currently available for the C# agent.

## Setting up a Launcher

You will need to start a listener for the agent to communicate with. You’ll notice that the “set” command now offers a dropdown list of suggested options and values. You can type `uselistener` to get a list of available listener options, but we will be using the http listener for this example.

![Dropdown menu for setting listener options](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_uselistener\_options.png?resize=656%2C448\&ssl=1)

Once the listener is started, you will need to generate a launcher to deploy the agent. The command `usestager` will display all the available stager options. At the moment, C# agents will only work with the csharp\_exe stager.

![Dropdown menu for available stagers](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_stager\_choices.png?resize=608%2C434\&ssl=1)

The csharp\_exe stager was originally created by [Elitest](https://github.com/elitest) as a C# stage 0 that launched a PowerShell agent. Hubbl3 created a purely C# stager that leverages the [Sharpire Project](https://github.com/0xbadjuju/Sharpire), which was an implementation of the Empire Agent in C#. The C# launcher, known as Sharpire, is packaged within this stager and can be changed based on setting the stager language to PowerShell or CSharp.

![Information page for the C# stager](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_stager\_options.png?resize=1106%2C946\&ssl=1)

![All options available for both PowerShell and C# launchers](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_stager\_info.png?resize=986%2C232\&ssl=1)

Many of the options traditionally used by PowerShell launchers are not currently available when creating a C# payload. For example, setting the Obfuscation and Bypasses will not affect the launchers generation and will be ignored.

![Message returned to Empire client when generating C# launcher](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_stager\_compile.png?resize=1170%2C90\&ssl=1)

New in Empire 4.0, files that are generated within Empire will be loaded into a client folder called “generated-stagers” which is located in the client directory.

![Generated stager directory for the Empire client](https://i2.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_exe\_location.png?resize=964%2C534\&ssl=1)

## Using the CSharp Agent

Launching the C# launcher is relatively simple. All that is needed is loading the file to the target machine and executing the .EXE. This will trigger the agent to execute and will initialize the staging in memory. The client will get a notification when the agent checks back in and will be displayed on the agents page.

![Table of active/inactive agents](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_agents.png?resize=1170%2C195\&ssl=1)

Typing `interact` will allow users to interact with the agent and send commands to it. A dropdown list of active agents will be displayed, so going to the agents page will not be necessary and so agent interaction can happen from any menu.

![Dropdown menu of Empire modules](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_modules.png?resize=1170%2C409\&ssl=1)

The command `usemodule` is how users will select modules to execute on the agent. Usemodule uses a keyword search to assist in selecting the correct module. Previously, a user had to type out the entire path to the module. The C# modules are compiled on the fly and sent across the C2 channel to the agent on the other side. A huge advantage of the way the C# modules were implemented is that it will allow C# agents to run either PowerShell or C# modules and vise versa.

![PowerShell module being executed through a C# agent](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_watson.png?resize=497%2C441\&ssl=1)

![Rubeus being compiled through the compiler and executed](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2021/05/e4\_csharp\_rubeus-edited-1.png?resize=558%2C726\&ssl=1)

![AMSI Bypass module from SharpSploit](https://i1.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_amsi\_bypass.png?resize=617%2C432\&ssl=1)

The interactive shell menu is a new feature that creates a session for a user to send PowerShell commands within. The interactive shell parses its current working directory and allows the user to get a similar feel to a PowerShell window.

![Interactive shell within an Empire agent](https://i0.wp.com/www.bc-security.org/wp-content/uploads/2019/05/e4\_csharp\_shell.png?resize=496%2C752\&ssl=1)
