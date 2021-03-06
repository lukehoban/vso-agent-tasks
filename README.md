#Tasks for vNext VSO Build System

Tasks which will be provided in the box in the new build system.

Also see the agent [here](https://github.com/Microsoft/vso-agent)

##Available Tasks
* Android
* Azure Cloud Deployment
* Azure PowerShell
* Azure WebSite Deployment
* CMake
* CmdScript
* Jake
* MSBuild
* PowerShell
* ProcessRunner
* ShellScript
* VSBuild
* VSTest
* Xcode Build

Coming Soon:

* Ant
* Maven
* Python

##Overview
Tasks are simply tool runners.  They know how to run MSBuild, VSTest, etc... in a first class way and handle return codes, how to treat std/err out, and how to write timeline records based on expected output.  Tasks also help you find an agent with the necessary tools (see demands below).

They also advertise what inputs they need in a first class way so the designer can take input.

Along with templates in the new build system, the goal is in many cases to simply do "New VS Build Definition", save and it just works.  Sometimes you may have to browse to a project file or supply a couple required inputs but it puts the user on rails for the common case.

##DevOps
We also have tasks for script runners such as PowerShell, cmd script, Shell Script, Jake (JavaScript) and Python is coming.  This allows users to run scripts *located in their source control system* ... the same scripts that devops run.  That is a key principle, devops == CI.

##Authoring
Tasks can be written in Powershell, ShellScript, javaScript or Python.  Tasks can carry multiple implementations for cases where you want to run PowerShell on Windows and a Shell Script for example on Linux or OSX.

##Capabilities and Demands
Tasks demand a tool or dependency that they run.  On configuration and startup, an agent registers it's capabilities with the server.  When you add a task to a definition it appends the demands for that definition.  When run, an agent is found with the corresponding capabilities from the configured pool of agents.