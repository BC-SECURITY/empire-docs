# Empire

![](https://user-images.githubusercontent.com/20302208/70022749-1ad2b080-154a-11ea-9d8c-1b42632fd9f9.jpg)

[![Docs](https://img.shields.io/badge/Wiki-Docs-green?style=plastic\&logo=wikipedia)](https://bc-security.gitbook.io/empire-wiki/) [![Twitter URL](https://img.shields.io/twitter/follow/BCSecurity1?style=plastic\&logo=twitter)](https://twitter.com/BCSecurity1) [![YouTube URL](https://img.shields.io/youtube/channel/views/UCIV4xSntF1h1bvFt8SUfzZg?style=plastic\&logo=youtube)](https://www.youtube.com/channel/UCIV4xSntF1h1bvFt8SUfzZg) [![Discord](https://img.shields.io/discord/716165691383873536?style=plastic\&logo=discord)](https://discord.gg/P8PZPyf) [![Donate](https://img.shields.io/badge/Donate-Sponsor-blue?style=plastic\&logo=github)](https://github.com/sponsors/BC-SECURITY) [![Blog](https://img.shields.io/badge/Blog-Read%20me-orange?style=plastic\&logo=wordpress)](https://www.bc-security.org/blog)

Empire is a post-exploitation and adversary emulation framework that is used to aid Red Teams and Penetration Testers. The Empire server is written in Python 3 and is modular to allow operator flexibility. Empire comes built-in with a client that can be used remotely to access the server. There is also a GUI available for remotely accessing the Empire server, [Starkiller](https://github.com/BC-SECURITY/Starkiller).

## Features

* Server/Client Architecture for Multiplayer Support
* Supports GUI & CLI Clients
* Fully encrypted communications
* HTTP/S, Malleable HTTP, OneDrive, Dropbox, and PHP Listeners
* Massive library (400+) of supported tools in PowerShell, C#, & Python
* Donut Integration for shellcode generation
* Modular plugin interface for custom server features
* Flexible module interface for adding new tools
* Integrated obfuscation using [ConfuserEx 2](https://github.com/mkaring/ConfuserEx) & [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation)
* In-memory .NET assembly execution
* Customizable Bypasses
* JA3/S and JARM Evasion
* MITRE ATT\&CK Integration
* Integrated Roslyn compiler (Thanks to [Covenant](https://github.com/cobbr/Covenant))
* Docker, Kali, Ubuntu, and Debian Install Support

## Agents

* PowerShell
* Python 3
* C#
* IronPython 3

## Modules

* [Assembly Execution](https://github.com/BC-SECURITY/Empire/blob/master/empire/server/data/module\_source/code\_execution/Invoke-Assembly.ps1)
* [BOF Execution](https://github.com/airbus-cert/Invoke-Bof)
* [Mimikatz](https://github.com/gentilkiwi/mimikatz)
* [Seatbelt](https://github.com/GhostPack/Seatbelt)
* [Rubeus](https://github.com/GhostPack/Rubeus)
* [SharpSploit](https://github.com/cobbr/SharpSploit)
* [Certify](https://github.com/GhostPack/Certify)
* [ProcessInjection](https://github.com/3xpl01tc0d3r/ProcessInjection)
* And Many More

## Sponsors

&#x20;      [<img src="https://user-images.githubusercontent.com/20302208/185246508-56f4f574-5a06-4a2c-ac62-320922588dcf.png" alt="" data-size="original">](https://www.sans.org/cyber-security-courses/red-team-operations-adversary-emulation/)&#x20;

&#x20;     [![](https://user-images.githubusercontent.com/20302208/208271681-235c914b-5359-426e-8a3d-903bbd018847.png)](https://www.cybrary.it/)   &#x20;

## Help us Improve!

This documentation was organized and built by the PowerShell Empire development team. It is neither complete nor perfect, so any suggestions, corrections, or additions from the community would be greatly appreciated. Please submit any changes as a pull request to the [empire-docs repository](https://github.com/BC-SECURITY/empire-docs).

{% @mailchimp/mailchimpSubscribe %}
