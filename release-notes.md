# Release Notes

## [4.7.0] - 2022-06-25
-   Update Python version on Dockerfile (@Vinnybod)
-   Add Python 3.10 to CI tests  (@Vinnybod)
-   Add a resource file command to the client (@Vinnybod)
-   Add PowerShell and C# to IronPython modules (@Cx01N)
-   Add ChiselServer, SocksProxyServer plugin as a submodule (@Cx01N)
-   Fixed Sharpire download function (@Cx01N)
-   Fixed spawnas to work with new bat file format (@Cx01N)
-   Fixed tasking error for IronPython launcher executable (@Cx01N)
-   Remove some python dependencies (@Vinnybod)
-   Make tkinter import failure a warning instead of a fatal error (@Vinnybod)

## [4.6.1] - 2022-06-10

-   Use a BC-Security fork of Donut to resolve a python 3.10 issue (@Cx01N)
-   Update reflective pick dlls (@Hubbl3)

## [4.6.0] - 2022-05-24

-   Added Certify C# module (@Cx01N)
-   Added embedded VNC client and launcher (@Cx01N)
-   Added obfuscate option to C# payloads (@Hubbl3)
-   Added global obfuscation to C# modules (@Cx01N)
-   Added -BasicParsing to .bat launcher (@X0RW3LL)
-   Added obfuscation to bat launcher for HTTP and HTTP COM (@Cx01N)
-   Added option to enable/disable JA3 evasion (@Cx01N)
-   Added JA3 evasion technique to Malleable HTTP (@Cx01N)
-   Added option to client config to remove borders on tables (@Cx01N)
-   Updated staging for agents (@Cx01N)
-   Updated confuser to confuserex 2 (@Cx01N)
-   Fixed nim install on Ubuntu by using choosenim installer (@vinnybod)
-   Converted reset.sh script to Python and add tests (@Vinnybod)
-   Add a `--reset` flag to the client (@Vinnybod)

## [4.5.5] - 2022-05-07

-   Fixed http bug in malleable, http-com, and onedrive listeners (@Cx01N)
-   Updated jq to 1.2.2 to avoid install errors (@Cx01N)

## [4.5.4] - 2022-04-26

-   Fixed typo from 4.5.3 with the bypass database model (@Vinnybod)

## [4.5.3] - 2022-04-24

-   Fixed issue where default_response is needed for external/generate_agent (@Cx01N)
-   Added check if bypass language is compatible (@Cx01N)
-   Added error message formatting for listeners and stagers (@Cx01N)
-   Added `zip` to the Dockerfile which is necessary to create ms files such as docx (@junquera)

## [4.5.2] - 2022-04-12

-   Fix string format errors in dbx listener (@awsmhacks)
-   Fix script_end error in schtasks.py (@harry-cmdzero)
-   Add workflows for doing the public releases (@Vinnybod)
-   Pull out common code from listeners to a listener_utils module (@Cx01N)
-   Fix missing script_path and fix variable references in service_stager and service_exe_stager (@harry-cmdzero)

## [4.5.1] - 2022-03-27

-   Fixed empire_config `yaml` property to include fields that don't exist on the config object (@Vinnybod)

## [4.5.0] - 2022-03-27

-   Updated changelog to use [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) (@Vinnybod).
-   Added tests for listener launchers (@Vinnybod).
-   Add a step to run the test suite on the Docker image itself (@Vinnybod)
-   Removed .plugin from the black configuration (@Vinnybod)
-   Removed random caps from backdoorlnk (@Cx01N)
-   Added html files for listener responses (@Cx01N)
-   Converted server config to a typed class (@Vinnybod)
-   Add keyword obfuscation to the config.yaml (@Vinnybod)
-   Fix proxy_creds variable name in bypassuac (@Cx01N)
-   Updated launcher_bat to use web request for launcher (@Cx01N)
-   updated malleable profiles with banzarloader (@Cx01N)
-   Added C# execution modules (@Cx01N)
-   Add tests for launcher code (@Vinnybod)
-   Split ls/dir command line to get the first element for ls/dir command (@CyrilleFranchet)
-   Updated lastwritetime on ls/dir command (@CyrilleFranchet)
-   Fix script_end variable on privesc/ask module (@CyrilleFranchet)
-   script_import will upload a file from the client's machine (@Cx01N)

## [4.4.1] - 2022-03-06

-   Fixed agent generation with custom headers (@Hubbl3)
-   Fixed missing quote in get_users.yaml (@Cx01N)
-   Fixed displaying info for plugins (@Cx01N)
-   Fixed legacy plugin loading to ignore folders (@Cx01N)
-   Removed http_mapi.ps1
-   Removed comment that global obfuscation and keyword obfuscation cannot be combined (@Cx01N)

## [4.4.0] - 2022-02-14

-   Added auto copy to clipboard feature (@Cx01N)
-   Added directory settings to yaml for downloads/stagers/obfuscated_modules (@Cx01N)
-   Added C# process injection module (Cx01N)
-   Added bypass yamls for PowerShell (@Hubbl3)
-   Added Black and Isort integration (@Vinnybod)
-   Added tests for loading and generating scripts with defaults (@Vinnybod)
-   Updated Psinject to use updated version of reflective pick and bypasses (@Hubbl3)
-   Fixed check for preobfuscation of files (Cx01N)
-   Fixed issue with plugins using tuple (@Vinnybod)
-   Removed random capitialization function for listeners (@Cx01N)
-   Removed meterpreter and mapi listeners (@Cx01N)
-   Powerview - added functions for group managed service accounts and fine grained pw pol (@jfmaes)

## [4.3.3] - 2022-01-24

-   Added a hook for when an agent is fully checked in (stage2) (@Vinnybod)

## [4.3.2] - 2022-01-14

-   Fixed issues with variables names in Mimikatz & Privesc modules (@sbrun)
-   Fixed issue with Invoke-Obfuscation not being properly called (@Cx01N)
-   Add dotnet install to dockerfile (@Vinnybod)

## [4.3.1] - 2022-01-08

-   Fixed issue with module variables referenced before assignment or undefined (@Vinnybod)
-   Fixed bug with Invoke-Seatbelt caused by variable name mismatch (@Vinnybod)
-   Fixed IronPython exit/shutdown issue (@Cx01N)
-   Fixed ToLower() bug in PowerShell agent when using route (@CyrilleFranchet)
-   Fixed multiline shell output bug (#491) (@CyrilleFranchet)
-   Added dir command to the file browser hook (@CyrilleFranchet)
-   Generate test account with secure rng (@moloch--)
-   Add Invoke-FodhelperProgIDs module (@m1m1k4tz)
-   Add Invoke-VeeamGetCreds module (@sadshade)

## [4.3.0] - 2021-12-23

-   Updated Invoke-Seatbelt, Invoke-Rubeus, & Invoke-WinPeas (@Cx01N)
-   Updated C# modules: Seatbelt, SharpSploit (@Cx01N)
-   Updated profiles to include APT29 (@Cx01N)
-   Updated Mimikatz to 20210810-2 (@Cx01N)
-   Updated reset script to remove c# tasks and generated-stagers (@Cx01N)
-   Added obfuscation options into Empire CLI (@Cx01N)
-   Added Invoke-BOF module (@Cx01N)
-   Added C# server plugin to run on startup (@Cx01N)
-   Added autostart plugin with options to config file (@Cx01N)
-   Added upload & download options for Empire CLI (@Cx01N)
-   Added Plugin folders and extensions (@Cx01N)
-   Added C# redirector (@Cx01N)
-   Added Invoke-DownloadFile (@Cx01N)
-   Added error message in client for file downloads >1MB (@Cx01N)
-   Moved NVNC and Sharpire as C# submodules (@Cx01N)
-   Fixed Invoke-Assembley (@Cx01N)
-   Fixed osx/clipboard & pilliageuser modules (@Cx01N)
-   Removed unused wiki workflows (@Cx01N)

## [4.2.0] - 2021-11-01

-   Added revershell & cmd launchers with reversehell (@Cx01N)
-   Added ironpython to compile through empire with embedded std lib (@Cx01N)
-   Added proxy (SOCKS/TOR/HTTP) pivots to python agents (@Cx01N)
-   Added notifications in bottom toolbar for plugins and agents (@Cx01N)
-   Added C# VNC server (@Cx01N)
-   Added extended rights for certificate templates (@daem0nc0re)
-   Added donut for shellcode generation (@Cx01N)
-   Updated WMI persistence and bug fixes (@janit0rjoe)
-   Updated covenant compiler (@Hubbl3)
-   Updated csharp powershell launcher to compile through empire (@Hubbl3)
-   Fixed formatting error in enable_rdp (@jamarir)
-   Fixed nim launcher to run internal to exe (@Cx01N)
-   Fixed misc python module errors (@Cx01N)
-   Fixed outfile message displaying wrong directory (@Cx01N)
-   Removed sRDI for shellcode (@Cx01N)

## [4.1.3] - 2021-09-28

-   Fixed output from files throwing a error for the client (@Cx01N)

## [4.1.2] - 2021-09-21

-   Removed pyminifier as a dependency to prevent install errors (@Cx01N)

## [4.1.1] - 2021-09-20

-   Add OutputFunction to dcsync_hashdump (@jamarir)
-   Convert file operations to use with syntax (@jamarir)
-   Added Invoke-IronPython3 and some OffensiveDLR fixes (@Cx01N)
-   Fix for (#476) - String indices error  ms16-032 & ms16-135 (@Cx01N)
-   Fix help menu text on the interact menu (@archcloudlabs)
-   Rework agent taskings in the client to not poll for a result (@Cx01N)
-   Added Python agents to the external/generate_agent module (@Cx01N)
-   Update add_sid_history module command (@ilanisme)

## [4.1.0] - 2021-08-29

-   Correct issue where install script would break depending on the current working directory (@Vinnybod)
-   Empire client now currently refreshes listener list after killing a listener (@Vinnybod)
-   Removed the wiki and added a link to the new docs (@Vinnybod)
-   Added the initial filtering/hooking feature (@Vinnybod)
-   Fix an issue where the docker builds would not run because it was deleting the database (@Vinnybod)
-   Added autocomplete for taskings in the Empire Client and added a command to view a specific task (@Cx01N)
-   Updated the OutputFunction feature to allow for arbitrary values (@Vinnybod)
-   Added an IronPython3 agent (@Cx01N)

## [4.0.2] - 2021-08-16

-   Added socketio messages to screenshot/download/upload (@Cx01N)
-   Added help message when no input is given to empire.py (@Cx01N)
-   Fixed missing slash for module directories (@Cx01N)
-   Fixed modules Get-SQLServerLoginDefaultPw and PortScan (@jamarir)
-   Fixed formatting bug in the options table on the listener menu (@Vinnybod)
-   Fixed querying retain-last-value config parameters (@ilanisme)
-   Fixed invalid concat on keylogs (@Cx01N)
-   Fixed mimikatz command and added suggested values (@Cx01N)
-   Fixed misc bugs (@Vinnybod)
-   Updated suggested values for stagers and reformatted code (@Cx01N)
-   Updated editlistener menu (@Vinnybod)
-   Removed client suppression for job started taskings (@Cx01N)

## [4.0.1] - 2021-07-19

-   Added API endpoints for sleep/jitter to agents (@Cx01N)
-   Added sleep command to CLI (@Cx01N)
-   Added sleep/jitter option to C# agents (@Hubbl3)
-   Fix for Invoke-Obfuscation installation
-   Added PrintNightmare module (@Cx01N)

## [4.0.0] - 2021-06-28

### Breaking Changes

-   Removed old Empire CLI and cmdloop from server (@Cx01N)
-   The credential create endpoint now accepts a single credential instead of a list
-   Some endpoints which were previously throwing 500s when not found, now properly return a 404
-   Plugin endpoints and socketio channels renamed to plural (plugin -> plugins) to match naming convention of other resources (@Vinnybod)

### New Features

-   Integrated server and client into Empire (@Cx01N, @Vinnybod)
-   Introduced C# agents (@Hubbl3)
-   Integrated Covenant Roslyn compiler for task compilation (@Hubbl3)
-   Covenant Task compatibility (@Hubbl3, @Vinnybod)
-   Added support for 'suggested values' on the server and auto completing the suggested values in the CLI (@Vinnybod)
-   Added new launch parameters for starting server/client (@Cx01N, @Vinnybod)
-   Added Offensive DLR Modules: IronPython, ClearScript, & Boolang (@Cx01N)
-   Added MS16-051 stager (@Cx01N)
-   Added Start-ProcessAsUser module (@Cx01N)
-   Added NTLM-Extract module (@Cx01N)
-   Added Invoke-SharpSecDump module (@Cx01N)
-   Added sriptimport and scriptcommand to API (@Cx01N)
-   Added auto generate certificate function to startup script (@Cx01N)
-   Added Invoke-SpoolSample (@Cx01N)
-   Added redirector chaining and proper tunneling (@Cx01N)
-   Updated pycrypto to pycryptodome (@Cx01N)
-   Updated PowerDump with AES NTLM hashes (@Cx01N)
-   Updated cert/install/reset script with new directories (@Cx01N)
-   Updated all modules to new YAML format (@Vinnybod, @Cx01N)
-   Updated to Mimikatz 2.2.0 20210531 X11 RDP Clients (@Cx01N)
-   Removed M2Crypto dependency (@Cx01N)
-   Simplified kill/remove commands and added 'all' and 'stale' options (@Cx01N)
-   Removed the need for manual database timestamp updates, merge taskings and results table to a single table (@Vinnybod)
-   Added a socketio event for when tasking results come back (@Vinnybod)
-   Readded rastamouse's bypass (@Cx01N)
-   Added a 'since' query parameter to the tasks endpoint for more efficient querying (@Vinnybod)
-   Added socketio tasking event handler to CLI for displaying task results in the interact menu (@Vinnybod)
-   Install script prompts for xar, bomutils, openjdk, and dotnet for a more streamlined install (@Vinnybod)
-   Install script now includes dotnet (@Vinnybod)
-   Dockerfile size decreased by ~1GB by only installing the essentials. There is a note in the README (@Vinnybod)
-   Made powershell bypasses dynamic. Now set with a single field `Bypasses` and they will be applied in the order provided (@Vinnybod)
-   Added API endpoints for managing bypasses (@Vinnybod)
-   Add processor architecture to powershell, csharp, and python agents (@Vinnybod)
-   Add a display command to interact menu (@Vinnybod)
-   Add additional endpoints for credential for get, update, and delete (@Vinnybod)
-   Add create, update, remove credential functionality to the CLI (@Cx01N)
-   Add an "output function" option on several modules (@jamarir)
-   Updated shellcoderdi to newest version (@Cx01N)
-   Added a Nim launcher (@Hubbl3)