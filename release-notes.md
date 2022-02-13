# Release Notes

```
1/24/2022
------------
- Version 4.3.3 Master Release
        - Added a hook for when an agent is fully checked in (stage2) (@Vinnybod)

1/14/2022
------------
- Version 4.3.2 Master Release
        - Fixed issues with variables names in Mimikatz & Privesc modules (@sbrun)
        - Fixed issue with Invoke-Obfuscation not being properly called (@Cx01N)
        - Add dotnet install to dockerfile (@Vinnybod)

1/8/2022
------------
- Version 4.3.1 Master Release
        - Fixed issue with module variables referenced before assignment or undefined (@Vinnybod)
        - Fixed bug with Invoke-Seatbelt caused by variable name mismatch (@Vinnybod)
        - Fixed IronPython exit/shutdown issue (@Cx01N)
        - Fixed ToLower() bug in PowerShell agent when using route (@CyrilleFranchet)
        - Fixed multiline shell output bug (#491) (@CyrilleFranchet)
        - Added dir command to the file browser hook (@CyrilleFranchet)
        - Generate test account with secure rng (@moloch--)
        - Add Invoke-FodhelperProgIDs module (@m1m1k4tz)
        - Add Invoke-VeeamGetCreds module (@sadshade)

12/23/2021
------------
- Version 4.3.0 Master Release
        - Updated Invoke-Seatbelt, Invoke-Rubeus, & Invoke-WinPeas (@Cx01N)
        - Updated C# modules: Seatbelt, SharpSploit (@Cx01N)
        - Updated profiles to include APT29 (@Cx01N)
        - Updated Mimikatz to 20210810-2 (@Cx01N)
        - Updated reset script to remove c# tasks and generated-stagers (@Cx01N)
        - Added obfuscation options into Empire CLI (@Cx01N)
        - Added Invoke-BOF module (@Cx01N)
        - Added C# server plugin to run on startup (@Cx01N)
        - Added autostart plugin with options to config file (@Cx01N)
        - Added upload & download options for Empire CLI (@Cx01N)
        - Added Plugin folders and extensions (@Cx01N)
        - Added C# redirector (@Cx01N)
        - Added Invoke-DownloadFile (@Cx01N)
        - Added error message in client for file downloads >1MB (@Cx01N)
        - Moved NVNC and Sharpire as C# submodules (@Cx01N)
        - Fixed Invoke-Assembley (@Cx01N)
        - Fixed osx/clipboard & pilliageuser modules (@Cx01N)
        - Removed unused wiki workflows (@Cx01N)

11/1/2021
------------
- Version 4.2.0 Master Release
        - Added revershell & cmd launchers with reversehell (@Cx01N)
        - Added ironpython to compile through empire with embedded std lib (@Cx01N)
        - Added proxy (SOCKS/TOR/HTTP) pivots to python agents (@Cx01N)
        - Added notifications in bottom toolbar for plugins and agents (@Cx01N)
        - Added C# VNC server (@Cx01N)
        - Added extended rights for certificate templates (@daem0nc0re)
        - Added donut for shellcode generation (@Cx01N)
        - Updated WMI persistence and bug fixes (@janit0rjoe)
        - Updated covenant compiler (@Hubbl3)
        - Updated csharp powershell launcher to compile through empire (@Hubbl3)
        - Fixed formatting error in enable_rdp (@jamarir)
        - Fixed nim launcher to run internal to exe (@Cx01N)
        - Fixed misc python module errors (@Cx01N)
        - Fixed outfile message displaying wrong directory (@Cx01N)
        - Removed sRDI for shellcode (@Cx01N)

9/28/2021
------------
- Version 4.1.3 Master Release
        - Fixed output from files throwing a error for the client (@Cx01N)

9/21/2021
------------
- Version 4.1.2 Master Release
        - Removed pyminifier as a dependency to prevent install errors (@Cx01N)

9/20/2021
------------
- Version 4.1.1 Master Release
        - Add OutputFunction to dcsync_hashdump (@jamarir)
        - Convert file operations to use with syntax (@jamarir)
        - Added Invoke-IronPython3 and some OffensiveDLR fixes (@Cx01N)
        - Fix for (#476) - String indices error  ms16-032 & ms16-135 (@Cx01N)
        - Fix help menu text on the interact menu (@archcloudlabs)
        - Rework agent taskings in the client to not poll for a result (@Cx01N)
        - Added Python agents to the external/generate_agent module (@Cx01N)
        - Update add_sid_history module command (@ilanisme)

8/29/2021
------------
- Version 4.1.0 Master Release
        - Correct issue where install script would break depending on the current working directory (@Vinnybod)
        - Empire client now currently refreshes listener list after killing a listener (@Vinnybod)
        - Removed the wiki and added a link to the new docs (@Vinnybod)
        - Added the initial filtering/hooking feature (@Vinnybod)
        - Fix an issue where the docker builds would not run because it was deleting the database (@Vinnybod)
        - Added autocomplete for taskings in the Empire Client and added a command to view a specific task (@Cx01N)
        - Updated the OutputFunction feature to allow for arbitrary values (@Vinnybod)
        - Added an IronPython3 agent (@Cx01N)


8/16/2021
------------
- Version 4.0.2 Master Release
       - Added socketio messages to screenshot/download/upload (@Cx01N)
       - Added help message when no input is given to empire.py (@Cx01N)
       - Fixed missing slash for module directories (@Cx01N)
       - Fixed modules Get-SQLServerLoginDefaultPw and PortScan (@jamarir)
       - Fixed formatting bug in the options table on the listener menu (@Vinnybod)
       - Fixed querying retain-last-value config parameters (@ilanisme)
       - Fixed invalid concat on keylogs (@Cx01N)
       - Fixed mimikatz command and added suggested values (@Cx01N)
       - Fixed misc bugs (@Vinnybod)
       - Updated suggested values for stagers and reformatted code (@Cx01N)
       - Updated editlistener menu (@Vinnybod)
       - Removed client suppression for job started taskings (@Cx01N)

7/19/2021
------------
- Version 4.0.1 Master Release
       - Added API endpoints for sleep/jitter to agents (@Cx01N)
       - Added sleep command to CLI (@Cx01N)
       - Added sleep/jitter option to C# agents (@Hubbl3)
       - Fix for Invoke-Obfuscation installation
       - Added PrintNightmare module (@Cx01N)

6/28/2021
------------
- Version 4.0.0 Master Release
    - Breaking Changes
        - Removed old Empire CLI and cmdloop from server (@Cx01N)
        - The credential create endpoint now accepts a single credential instead of a list
        - Some endpoints which were previously throwing 500s when not found, now properly return a 404
        - Plugin endpoints and socketio channels renamed to plural (plugin -> plugins) to match naming convention of other resources (@Vinnybod)
    - New Features
        - Integrated server and client into Empire (@Cx01N, @Vinnybod)
        - Introduced C# agents (@Hubbl3)
        - Integrated Covenant Roslyn compiler for task compilation (@Hubbl3)
        - Covenant Task compatibility (@Hubbl3, @Vinnybod) 
        - Added support for 'suggested values' on the server and auto completing the suggested values in the CLI (@Vinnybod)
        - Added new launch parameters for starting server/client (@Cx01N, @Vinnybod)
        - Added Offensive DLR Modules: IronPython, ClearScript, & Boolang (@Cx01N)
        - Added MS16-051 stager (@Cx01N)
        - Added Start-ProcessAsUser module (@Cx01N)
        - Added NTLM-Extract module (@Cx01N)
        - Added Invoke-SharpSecDump module (@Cx01N)
        - Added sriptimport and scriptcommand to API (@Cx01N)
        - Added auto generate certificate function to startup script (@Cx01N)
        - Added Invoke-SpoolSample (@Cx01N)
        - Added redirector chaining and proper tunneling (@Cx01N)
        - Updated pycrypto to pycryptodome (@Cx01N)
        - Updated PowerDump with AES NTLM hashes (@Cx01N)
        - Updated cert/install/reset script with new directories (@Cx01N)
        - Updated all modules to new YAML format (@Vinnybod, @Cx01N)
        - Updated to Mimikatz 2.2.0 20210531 X11 RDP Clients (@Cx01N)
        - Removed M2Crypto dependency (@Cx01N)
        - Simplified kill/remove commands and added 'all' and 'stale' options (@Cx01N)
        - Removed the need for manual database timestamp updates, merge taskings and results table to a single table (@Vinnybod)
        - Added a socketio event for when tasking results come back (@Vinnybod)
        - Readded rastamouse's bypass (@Cx01N)
        - Added a 'since' query parameter to the tasks endpoint for more efficient querying (@Vinnybod)
        - Added socketio tasking event handler to CLI for displaying task results in the interact menu (@Vinnybod)
        - Install script prompts for xar, bomutils, openjdk, and dotnet for a more streamlined install (@Vinnybod)
        - Install script now includes dotnet (@Vinnybod)
        - Dockerfile size decreased by ~1GB by only installing the essentials. There is a note in the README (@Vinnybod)
        - Made powershell bypasses dynamic. Now set with a single field `Bypasses` and they will be applied in the order provided (@Vinnybod)
        - Added API endpoints for managing bypasses (@Vinnybod)
        - Add processor architecture to powershell, csharp, and python agents (@Vinnybod)
        - Add a display command to interact menu (@Vinnybod)
        - Add additional endpoints for credential for get, update, and delete (@Vinnybod)
        - Add create, update, remove credential functionality to the CLI (@Cx01N)
        - Add an "output function" option on several modules (@jamarir)
        - Updated shellcoderdi to newest version (@Cx01N)
        - Added a Nim launcher (@Hubbl3)

3/28/2021
------------
- Version 3.8.2 Master Release
       - Fixed issue with try/catch preventing agent connections for http_hop/http listeners (@Cx01N)

3/22/2021
------------
- Version 3.8.1 Master Release
       - Fixed http_hop listener options not being copied properly (@Cx01N)

3/7/2021
------------
- Version 3.8.0 Master Release
        - Fix for literal comparison warnings in Python agent - #428 (@mattbogenberger)
        - Add an Invoke-SweetPotato module - #433 (@Invoke-Mimikatz)
        - Fix failed ticket generation in Invoke-Kerberoast - #434 (@Pen-Git)
        - Add ability to specify the bind IP for RESTful API - #431 (@meldridge)

2/5/2021
------------
- Version 3.7.2 Master Release
        - Fixed Malleable C2 issue where netbios/netbiosu transformations used excessive resources (@Cx01N)
        - Fixed error when loading http_hop listener options (@Cx01N)

1/27/2021
------------
- Version 3.7.1 Master Release
        - Added Kali message to main menu

1/18/2021
------------
- Version 3.7.0 Master Release
        - Revamped backend database from direct sqlite3 to SQLAlchemy (@Cx01N, @Vinnybod)
        - Added new Empire CLI to packaging (@Vinnybod)
        - Added malleable C2 profiles to empire directory: /data/profiles (@Cx01N)
        - Added --teamserver option to launcher (@Cx01N)
        - Added support for logging into Empire from multiple locations (@Vinnybod)
        - Added Invoke-WireTap (@Cx01N)
        - Added Invoke-SauronEye (@Cx01N)
        - Added Invoke-SharpLoginPrompt (@Cx01N)
        - Fixed OneDrive Listener with new database (@Cx01N)
        - Removed need to run setup database script (@Vinnybod)
        - Updated docker image to use the locked dependencies in pyproject.toml (@Vinnybod)

12/18/2020
------------
- Version 3.6.3 Master Release
        - Added save path to download file message - #414 (@meldridge)
        - Updated installation file formatting - #410 (@Pernat1y)
        - Fixed python 3.9.1 issue with deprecated base64 function - #422 (@brimstone)
        - Fixed dump creds and hash not being logged in credentials properly - #423 (@Cx01N)

11/27/2020
------------
- Version 3.6.2 Master Release
        - Added python support for HTTP malleable listener - #404 (@adamczi)
        - Added new admin menu API endpoints - #403 (@Vinnybod, @Cx01N)
        - Added chat server for Starkiller and new Empire CLI integration - #403 (@Vinnybod, @Cx01N)
        - Added module PrivescCheck - #401 (@Invoke-Mimikatz)
        - Fixed error in malleable profiles when http-stager is not defined - #407 (@Cx01N)

11/16/2020
------------
- Version 3.6.1 Master Release
        - Added editable wiki and sync option to repo - #398 (@Cx01N)
        - Fixed byte error in python/collection/osx/prompt - #396 (@Cx01N)
        - Fixed clear option issue for malleable listener - #393 (@Cx01N)
        - Added update_comms, killdate, and workinghours endpoints - #399 (@Cx01N)

11/9/2020
------------
- Version 3.6.0 Master Release
        - Added new API endpoints for user and agent notes - #383 (@Cx01N)
        - Added (readded) PowerView function add-netuser - #381 (@Cx01N)
        - Added Invoke-SharpChisel module - #368 (@Invoke-Mimikatz)
        - Added command option to psremoting and smbexec - #380 (@Invoke-Mimikatz)
        - Added option to use multiple redirector listeners and chaining - #389 (@Cx01N)
        - Added Invoke-Assembly module - #376 (@Invoke-Mimikatz)
        - Updated API endpoints for dynamic plugin calls - #383 (@Cx01N)
        - Updated plugin and module templates - #384 (@Cx01N)
        - Fixed smbscanner to work on Windows 10 - #380 (@Invoke-Mimikatz)
        - Fixed update agent comms (updatecomms) not properly changing - #382 (@Cx01N)
        - Fixed download endpoint formatting and error handling - #383 (@Cx01N)
        - Fixed issue with passing arguments to Get-DomainSID module - #374 (@mjokic)
        - Fixed bat file length limit issue - #385 (@Hubbl3)

10/22/2020
------------
- Version 3.5.2 Master Release
        - Fixed token manipulation (steal_token) functionality in Windows 10 - #355 (@Hubbl3)
        - Fixed lateral movement module New-GPOImmediateTask - #362 (@Cx01N)
        - Fixed Invoke-PSRemoting blocking current agent - #359 (@mjokic)

10/14/2020
------------
- Version 3.5.1 Master Release
        - Fixed Invoke-Obfuscation in Kali/Dockers - #348 (@Cx01N, @Hubbl3)
        - Refactored /api/map endpoint - #337 (@mattaereal)

10/13/2020
------------
- Version 3.5.0 Master Release
        - Added socketio notifications for Starkiller - #335 (@vinnybod)
        - Added Invoke-ZeroLogon - #333 (@Cx01N)
        - Added Invoke-SocksProxy - #332 (@Cx01N, @Hubbl3)
        - Added powercat module - #319 (@Cx01N)
        - Added powermad modules - #329 (@snovvcrash)
        - Added self cleanup functionality to plugins - #332 (@Hubbl3)
        - Updated Mimikatz 2.2.0 20200918 ZeroLogon - #330 (@Cx01N)
        - Fixed dropbox listener and staging issues - #327 (@Cx01N)
        - Fixed docker missing pyparsing in requirements.txt - #324 (@Cx01N)
        - Fixed modules with missing MITRE ATT&CK techniques - #321 (@Cx01N)
        - Fixed issue with inputs not being assigned color in helpers.py - #332 (@Cx01N)

9/15/2020
------------
- Version 3.4.0 Master Release
        - Added Malleable C2 HTTP Listener - #287 (@Johneiser, @Cx01N, @Hubbl3)
        - Added reflective load ability for files - #309 (@Hubbl3)
        - Added Invoke-DomainPasswordSpray - #295 (@Cx01N)
        - Added Invoke-WinPEAS - #293 (@Cx01N)
        - Added Invoke-Watson - #294 (@Cx01N)
        - Added plugins being loaded at startup - #301 (@Cx01N)
        - Updated moduleName to display full directory - #299 (@Cx01N)
        - Updated info in Invoke-SMBExec to indicate single target - #286 (@Cx01N)
        - Updated Slack API notifications to webhooks - #303 (@Cx01N)
        - Fixed spaces for IIS default page in HTTP listener - #302 (@adamczi)
        - Fixed agent spawning issue with MS-16-032 - #292 (@Cx01N)
        - Fixed min language version for modules (@Cx01N)
        - Fixed CLI stager incorrectly shutting down - #198 (@Cx01N)
        - Fixed error message from active agents during shutdown - #308 (@Cx01N)

9/8/2020
------------
- Version 3.4.0-RC2
        - Added plugins being loaded at startup - #301 (@Cx01N)
        - Fixed CLI stager incorrectly shutting down - #198 (@Cx01N)
        - Updated moduleName to display full directory - #299 (@Cx01N)
        - Updated info in Invoke-SMBExec to indicate single target - #286 (@Cx01N)

9/1/2020
------------
- Version 3.4.0-RC1
        - Added Malleable C2 HTTP Listener - #287 (@Johneiser, @Cx01N, @Hubbl3)
    	- Added Invoke-DomainPasswordSpray - #295 (@Cx01N)
    	- Added Invoke-WinPEAS - #293 (@Cx01N)
    	- Added Invoke-Watson - #294 (@Cx01N)
    	- Fixed agent spawning issue with MS-16-032 - #292 (@Cx01N)
    	- Fixed min language version for modules (@Cx01N)

8/18/2020
------------
- Version 3.3.4 Master Release
    	- Fixed preobfuscate error: could not read module source path - #282 (@Cx01N)
    	- Fixed issues http_foreign listener issue - #283 (@Cx01N)

8/12/2020
------------
- Version 3.3.3 Master Release
    	- Added get_gpo_computer module - #271 (@bytebl33d3r)
    	- Added port forwarding module - #265 (@snovvcrash)
    	- Updated HTTP/HTTP_com listeners to closer resemble IIS 7.5 - #277 (@adamczi)
    	- Updated lateral movements (invoke_smbexec/invoke_dcom/invoke_executemsbuild/invoke_wmi) to include option for custom commands - #247 (@Invoke-Mimikatz)
    	- Updated Mimikatz 2.2.0 20200809 AzureAd x-ms-RefreshTokenCredential & DPAPI everywhere - #279 (@Cx01N)
    	- Fixed issue with duplicate results in db - #266 (@bytebl33d3r)
    	- Fixed empty token issue in API - #274 (@Vinnybod)
    	- Fixed missing keyword argument in ETWBypass - #273 (@Cx01N)

8/5/2020
------------
- Version 3.3.2 Master Release
	- Added Event Tracing for Windows (ETW) Bypass to stagers - #269 (@Hubbl3)
	- Updated Mimikatz 20200805 CloudAP Key Derivation - #268 (@Cx01N)
	- Updated Invoke-Kerberoast to John The Ripper format - #263 (@kazkansouh)
	- Fixed indentation issues in schtasks - #267 (@adamczi)

7/20/2020
------------
- Version 3.3.1 Master Release
	- Updated Mimikatz to 20200715 NPLogonNotify passwords - #260 (@Cx01N)
	- Fixed syntax errors in Get-GPPPassword and MS16-135 - #259 (@PaulWhitingS2)
	- Fixed missing keylogger character issue - #252 (@Cx01N)
	- Fixed missing agentPSversion variable - #262 (@Cx01N)

7/10/2020
------------
- Version 3.3.0 Master Release
	- Added MITRE Attack Techniques/Software Functionality - #242 (@Cx01N)
	- Added keyword obfuscation option to modules - #244 (@Hubbl3)
	- Added Invoke-Rubeus - #238 (@Cx01N)
	- Added Filescraper commands - #236 (@vinnybod)
	- Added AMSIBypass option to modules that generate new agents - #244 (@Hubbl3)
	- Fixed timestamp format issue in agents list - #235 (@Cx01N)
	- Fixed external/generate_agent generation issue - #240 (@Cx01N)
	- Removed unused imports + few random fixes - #241 (@Cx01N)

6/7/2020
------------
- Version 3.2.3 Master Release
	- Added Invoke-Seatbelt module - #222 (@Cx01N)
	- Added timezone awareness timestamps - #220 (@Vinnybod)
	- Added MITRE ATT&CK techniques and software IDs to modules - #223 (@Cx01N)

5/25/2020
------------
- Version 3.2.2 Master Release
	- Added Invoke-PrintDemon module - #210 (@Hubbl3, @Cx01N)
	- Updated Mimikatz 2.2.0 20200519 Windows 10 2004 - #211 (build 19041) (@Cx01N)
	- Fixed youtube URL in trollsploit/thunderstruck - #207(@Gutters2Gardens)
	- Added API endpoints for plugins - #213 (@Hubbl3)
	- Fixed keylogger issue when writing to file - #206 (@Cx01N)

5/10/2020
------------
- Version 3.2.1 Master Release
	- Updated reflective PE injection to work in Windows 10 - #202 (@Hubbl3)
	- Updated Mimikatz to 20200502 TPM, IF & XOR - #200 (@Cx01N)
	- Added option to run Mimikatz commands as non-elevated user - #193 (@Cx01N)
	- Added safe string cast for reporting log - #203 (@Vinnybod)
	- Fixed byte encoding error in invoke_wmi_debugger - #203 (@Cx01N)
	- Removed Get-ExploitableSystem due to function being removed from PowerView- #194 (@Cx01N)
	- Replaced Invoke-ReflectivePEInjection.ps1 with newer version - #202 (@Hubbl3)

4/26/2020
------------
- Version 3.2.0 Master Release
	- Added SharpChromium module - #185 (@tyraniter)
	- Added BloodHound 3 module - #123 (@RaphAlmeida)
	- Updated to Mimikatz 2.2.0 20200308 Masterkey - #189 (@Cx01N)
	- Fixed issue with first character in randomizing function names - #169 (@Hubbl3)
	- Fixed encoding error for slack tokens - #181 (@Cx01N)
	- Fixed typo in python/persistence/multi/desktopfile.py - #182 (@Vinnybod)
	- install.sh - Updated Debian 10 powershell install and python3 library installs - #187 (@Cx01N, @Vinnybod)
	- Added single user endpoint to API - #188 (@Vinnybod)
	- Updated default python launcher to use | python3 - #184 (@Cx01N)
	- Converted python modules to python3 formatting - #187 (@Cx01N)
	- Removed duplicate exec in python agent tasking - #187 (@Cx01N)
	- Fixed errors in collection/linux/hashdump - #187 (@Cx01N)
	- Fixed errors in osx/native-screenshot - #187 (@Cx01N)
	- Fixed error handling issue for failed python modules - #187 (@Cx01N)
	- Added prompt before reset script is ran using --reset flag - #190 (@Cx01N)
	- Docker builds no longer require a database reset the first time and the certs are already generated. Default cmd starts the rest api. - #188 (@vinnybod)

4/13/2020
------------
- Version 3.1.5 Master Release
	- Fixed macro staging bug - #164 (@Hubbl3)
	- Fixed TLS cipher suite issue with PowerShell 2 - #155 (@tyraniter)
	- Updated API reporting for Starkiller integration - #168 (@Cx01N)

4/4/2020
------------
- Version 3.1.4 Master Release
	- Fixed non-ascii filename download error - #141 (@tyraniter)
	- Updated payload evasion against Defender - #147 (@Hubbl3)
	- Added reset flag to empire launcher - #147 (@Cx01N)
	- Replaced imp package with importlib - #108 (@Cx01N)
	- Fixed internal monologue issue with only running once - #43 (@Cx01N)
	- Fixed ascii encode error in powerbreach modules - #150 (@CykuTW)

3/22/2020
------------
- Version 3.1.3 Master Release
	- Fixed errors with OneDrive listener - #40 (@Cx01N)
	- Fixed REST API get config error - #131 (@chenxiangfang)
	- Increased timer for stale agent checkins - #130 (@Cx01N)

3/13/2020
------------
- Version 3.1.2 Master Release
	- Fixed REST login error 500 on some version of SQLite - #120 (@justsly)
	- Fixed generate launcher bug for redirector listener - #125 (@RedBulletTooling)

3/8/2020
------------
- Version 3.1.1 Master Release
	- Updated the /me endpoint that was added in 3.1.0 to return the full user object (@Vinnybod)
	- Updated install script for Kali Powershell install - #118 (@Vinnybod)

3/2/2020
------------
- Version 3.1.0 Master Release
	- Added Multi-user Collaboration to API - #105 (@Cx01N & @Vinnybod)
	- Updated to Mimikatz 2.2.0 20200208 - #104 (@Cx01N)
	- Fixed incorrect header on python response packet (@Cx01N)
	- Added progress bar to download function - #106 (@Cx01N)
	- Expanded API functionality (@Vinnybod)
	- Fixed str/byte in empire.py - #103 (@hypnoticpattern)
	- Fixed typos in helpers.py - #103 (@hypnoticpattern)
	- Fixed unsupported formatting for null hostname - #103 (@hypnoticpattern)
	- Added function name aliasing to Invoke-Empire & Mimikatz - #109 (@Hubbl3)

2/6/2020
------------
- Version 3.0.7 Master Release
	- Fixed string decode error in API - #92 (@Cx01N)
	- Fixed python3 conversion errors in backdoorlnkmacro, multi/war, osx/dylib, osx/pkg, and osx/macho launchers (@Cx01N & @hypnoticpattern)
	- Fixed exception error in autorun queue - #95 (@Cx01N)
	- Fixed report generation and SQL database errors (@Vinnybod & @Cx01N)

1/31/2020
------------
- Version 3.0.6 Master Release
	- Fixed osx stager generation byte/str errors - #84 (@hypnoticpattern)
	- Fixed osx appbundle generation which was stripping the wrong string - #84 (@hypnoticpattern)
	- Removed future imports from python3 launcher, so it works without any extra libraries - #81 (@Cx01N)
	- Staging key no longer needs to be exactly 32 characters - #85 (@Cx01N)
	- Add "stale" property to agents endpoint - #90 (@Vinnybod)
	- Agents endpoint now returns agents without failing due to session_key encoding - #90 (@Vinnybod)
	- Fixed an indentation bug in aes.py (@Cx01N)

1/21/2020
------------
- Version 3.0.5 Master Release
	- Fixed setup_database.py python3 issue - #75 (@linxon)
	- Added loaded listener types to API - #78 (@Vinnybod)
	- Fixed python launcherBase (@Cx01N)
	- Updated Python 3.8 compatibility in stager - #72 (@complana)
	- Fixed Powerup Invoke-allchecks issue - #64 (@SkiddieTech)
	- Fixed shellcode stager - #76 (@Hubbl3)
	- Fixed binary upload error - #55 (@Hubbl3)
	- Fixed multi/bash error (@Cx01N)

1/14/2020
------------
- Version 3.0.4 Master Release
	- Fixed data/agents.py error - #70 (@sbrun)

1/13/2020
------------
- Version 3.0.3 Master Release
	- Updated RESTful API to Python 3 - #49 (@Cx01N)
	- Fixed credential issue - #65 (@Hubbl3)
	- Fixed python agent - #52 (@Cx01N, @Hubbl3)
	- Cleaned up install files - #58 (@Vinnybod)

1/7/2020
------------
- Version 3.0.2 Master Release
	- Updated SystemRandom() and maintain API compatibility - #29 (@moloch--)
	- Fixed invoke-shell code (@Hubbl3)
	- Fixed meterpreter stager generation - #59 (@Hubbl3)
	- Fixed lnk and dll launchers - #57 (@C01N)
	- Fixed multi/macro launcher - #60 (@Hubbl3)
	- Updated orphaned agent handling - #56 (@Hubbl3)
	- Fixed pip3 install - #50 (@Hubbl3)
	- Removed unsupported invoke-shellcode options (@Hubbl3)

12/29/2019
------------
- Version 3.0.1 Master Release
	- Fixed sysinfo error - #36 (@Invoke-Mimikatz)
	- Fixed Debian 10.x docker - #38 (@Vinnybod)
	- Fixed windows/macro stager error - #30 (@Cx01N)
	- Fixed upload file error - #30 (@Cx01N)
	- Fixed meterpreter error - #42 (@Cx01N)
	- Fixed download file error (@Cx01N)
	- Fixed scriptcmd error - #45 (@Invoke-Mimikatz)
	- Fixed print creds error - #31 (@Hubbl3)
	- Cleaned up print results (@Cx01N)
	- Fixed long running module issue - #16 (@Hubbl3)

Thank you to the contributors for spending time debugging with our team.
Please contact us at Empire@bc-security.org if credit is incorrectly cited.

12/22/2019
------------
- Version 3.0 Master Release
	- Added Python 2.6/7 and 3.x compatibility (@Cx01N, @Hubbl3, @Vinnybod)
	- Improved Windows Defender Evasion (@Hubbl3)
	- Updated mimikatz binary in Invoke-Mimikatz to version 2.2.0 20191125 (@Cx01N)
	- Fixed port assignment feature to listeners (@Cx01N)
	- Fixed issues with http_Hop listener (@Cx01N)
	- Fixed issues with redirector listener (@Cx01N)
	- Fixed typos in default http listener payloads (@Hubbl3)
	- Fixed psinject AV recognition (@Hubbl3) 
	- Updated Invoke-Obfuscation to version 1.8 (@phra)
	- Updated Invoke-Kerberoast (@Zero1t0) 
	- Added ability to uselisteners on main menu (@Cx01N, @Hubbl3)
	- Added Get-Subnet_Ranges (@benichmt1)
	- Added Get-WinUpdates (@classity)
	- Added Get-KerberosServiceTIcket (@OneLogicalMyth)
	- Added Invoke-RID_Hijack (@r4wd3r)
	- Added Invoke-internal_monologue (@audibleblink)
	- Added Get-LAPSPasswords (@ippsec)
	- Added Invoke-SMBLogin (@mvelazc0)
	- Added Sherlock (@ippsec)
	- Added Outlook Sandbox Evasion for Windows Macro launcher (@Cx01N, @Hubbl3)
	- Added Randomized JA3/S signature (@Hubbl3)
	- Added AMSI Bypass based on Tal Liberman's AMSI Bypass (@Hubbl3)
	- Added Invoke-CredentialPhisher (@quickbreach)
	- Made Security Bypasses configurable for launchers (@phra)
	- Updated Readme to include install instruction, EOL of Core Developer support, new contribution rules (@Hubbl3)
	- Added OSX shellcode stager (@johneiser)
	- Added Invoke-Phant0m (@leesoh)
	- Added Get-AppLockerConfig (@matterpreter)
	- Added HostRecon (@RootUp)
	- Added more informative PS agent directory listing (@winnie22)

Credit was given based on Commit Author if something is credited incorrectly or we missed an update 
please contact us at info@bc-security.org 

03/15/2018
------------
- Version 2.5 Master Release
	- Patched launcher generation bug
	- Added OSX Mic record module #893 (@s0lst1c3)
	- More robust password handling in ssh_command and ssh_launcher modules (@retro-engineer)
	- Updated server responses for http listener (@xorrior) 
	- Template search bug fix (@DakotaNelson)
	- bug fix to properly assign taskIDs (@shakagoolu)
	- Kali & powershell install fix (@SadProcessor)
	- Overhaul events system to provide more descriptive messages and accurate logging of events (@DakotaNelson)
	- Added macro that backdoors lnk files (@G0ldenGunSec)
	- Bug fix for invoke_psexec module when using custom commands (@ThePirateWhoSmellsOfSunflowers)
	- Added capability to generate a vs studio project file to compile a csharp executable/launcher (@elitest)
	- Added capability to enable/disable/delete listeners (@mr64bit)
	- Added report generation (@bneg)
	- Updated http_com listener to server IIS7 default page and added response headers to evade nessus scans (@s0lst1c3)
	- Fixed script generation bug for all powerview modules (@xorrior)
	- Modify the minidump module to allow for non-admin users to dump memory (@ThePirateWhoSmellsOfSunflowers)
	- Removed background downloads feature for powershell agent 
	- Added linux persistence module via the ~/.config/autostart directory (@jarrodcoulter)
	- Added download command to REST API (@shakagoolu)
	- Added support for '&&' and ';' characters in shell commands for python agent (@cleb-sfdcsec)
	- Added wireless network information to the osx/situational_awareness/host module. (@import-au)
	- Added keychain dump module that uses the security utility (@import-au)
	- Added shellcode stagers and the 'shinject' module (@xorrior, @monoxgas)
	- Added a sleep and jitter parameter to the Invoke-Kerberoast module (@Retrospected)
	- Added capability to update agent comms dynamically (@xorrior)
	- Added onedrive listener for powershell agent (@mr64bit)
	- Added opsec-safe aliases for ls, pwd, rm, mkdir, whoami, and getuid in the python agent 
	- Updated office macro stager for python agent (@import-au)

01/04/2018
------------
- Version 2.4 Master Release
	- Added Kevin Robertson's Invoke-SMBExec.ps1
	- Update Invoke-DCOM
	- Added Dockerfile, Docker Hub images, Build/Release scripts (@killswitch-gui)
	- Updated README for cleaner install instructions with new options
	- Support for plugins (@DakotaNelson)
	- Fixed module output bug #792 (@clr2of8)
	- Added MSBuild XML Launcher (@p3nt4)
	- Added module to extract private keys (@mlinton)
	- Added cross-platform macro (@malcomvetter)
	- Proxy settings fix #788 (@m7x)
	- Updated mimikatz binary in Invoke-Mimikatz to version 2.1.1 20171106
	- Updated install.sh
	- Updated PowerView.ps1 source and all related modules 
	- powershell install fix, Invoke-obfuscation updates, Improve ScriptBlockLogging bypass (@cobbr)
	- Custom header support for http_com listener (@leeloobeek)
	- Allow for distinct values between the Host and Port options (@jetsecurity) 
	- Added pwd and cat aliases for the python agent (@xorrior)
	- Added redirector listener, formerly known as the redirector module (@xorrior)
	- Added exception handling for wmi call in powershell stager #827
	- Get Agent Results REST API call returns taskID #854 (@byt3bl33d3r)
	- Added templating engine (@DakotaNelson)
	- Removed pyCrypto dependencies (@elitest)
	- http listener update: Updated defaults response logic and default page to match IIS 7.5 #890 (@s0lst1c3)
	- Added module for nix aws ec2 metadata (@TweekFawkes)

10/29/2017
------------
- Version 2.3 Master Release
	— Fix for #755
	— Merge PR from byt3bl33d3r for TLS version
	— Removed option to set chunk size for file downloads
	— Fix for #729 (Unable to download files with spaces)
	— Fix renegotiation in powershell agent. Patched python agent to exit on 401 response.
	— Fix for #774 (Fix pyinstaller module)
	— Added resource scripts capability (Carrie Roberts)
	— Fix for #749 (Fix external agent modules)
	— Fix for #369 (Fixed http_hop listener with ssl and self-signed certificate)
	— Merge Invoke-PowerDump fix
	— Merge fixes for 718 (Fix generate function signature for module @nikaiw)
	— Merge fixes for 762 (Code cleanup from EmPyre @elitest)
	— Merge ntds execution module (@hightopfade)
	— Updated generate function signatures in all modules
	— Fixed stagerURI option (rvrsh3ll)

10/12/2017
--------
- Version 2.2 Master Release
	- Update crontab to work hourly #667
	- Update keylogger to log to disk on server side by @clr2of8 
	- Fix macro launcher #681
	- Fixes vbscript string literal quoting. #702
	- Add option to host a stager payload in the http listener @424f424f
	- Add @enigma0x3 Token Manipulation script as a BypassUAC module @424f424f
	- Hide true host name when using domain fronting #730 @clr2of8
	- Fixed custom proxy config in launcher code #728 @dirkjanm
	- generate_upload function added to Stagers #722 @hightopfade
	- Aes kerberoast #725 @elitest
	- DBX Improvements (SOCKS, Hide window via WindowHandler) #721 @IljaSchumacher
	- Improved ScriptBlock logging bypasses #740 @cobbr_io
	- Slack Integration - Notification for new Agents #737 @dchrastil
	- Improve Get-ChromeDump #734 @ThePirateWhoSmellsOfSunFlowers
	- Fix Eternal Blue Issue #656
	- Merge Invoke-Kerberoast: Print hashes only. Formatting with a text editor is no longer required. #663
	- Fix Macro syntax error per @utkusen issue #664 
	- Fix Better powershell install, obfuscation bug fixes, fixed vbs/macro launchers #686 @cobbr
	- Fix creds manual add parsing with whitespace in password
	- Fix validate length parameter attribute for Invoke-PSInject.ps1d

8/28/2017
--------
- Version 2.1 Master Release
	-Add get schwifty trollsploit module @424f424f
	-Add -sta flag to launcher @xorrior
	-Fixed hardcoded cert path @xorrior
	-Fix for #567
	-Merge Capture OSX credentials from Prompt Module in Empire DB @malcomvetter.
	-Rest API fixups #526 @byt3bl33d3r
	-Added MS16-135 exploit module @ThePirateWhoSmellsOfSunflowers
	-Updated Bloodhound Ingestion module @424f424f
	-Added Dropbox exfil module @ktevora1
	-Added EternalBlue module @ktevora1
	-Fix SSL certificate issue with Flask @diskonnect
	-Modify staging to handle unicode characters @killswitch-GUI
	-Add wmi_updater module #509 @tristandostaler
	-Add DropBox exfil module #557 @e0x70i
	-Fix Unexpected error: <class 'struct.error'> run empire #567
	-Fix SSL Intermediate Certificates to support Domain Fronting #569 @dchrastil
	-Add ‘SandboxMode’ to evade Apple Sandbox protection on applescript #578 @dchrastil
	-Add Obfuscated Empire #597 @cobbr
	-Add Bypass ScriptBlock Logging #603 @cobbr
	-Add mimipenguin module @424f424f
	-Add dyld_print_to_file Mac privesc @checkyfuntime
	-Added manual proxy specifications @xorrior
	-Fix libssl-dev and libssl1.0.0 packages @xorrior
	-Add backgrounding for downloads in PowerShell agent @xorrior
	-Fix warning patch in http listener @viss
	-Update Invoke-Kerberoast @424f424f
	-Tab complete shows elevated modules: #599
	- Additional bypassUAC modules added: #596
	- Added show uac level module #609
	- Fixed shebangs: #640

5/15/2017
---------
-Version 2.0 Master Release
	-Merge of Empyre and Empire projects
	-Fix REST API
	-Add Dropbox Listener
	-Add support for IPv6 agents and listener
	-Add DCOM lateral movement module
	-Add module - Sudo Piggyback + Mail Persistence + Bash Profile Backdoor #357
	-Add USB ETW Keylogger #396
	-Fix dcos modules and fixed pyinstaller  #403
	-Fix agent staging over http_hop listeners #404
	-Fixed Get-SPNTicket multiple user SPNs bug #405
	-Fix issue with Invoke-Shellcode Meterpreter stager #414
	-Fix code_execution/invoke_reflectivepeinjection hangs empire if an invalid path is provided to DllPath #421
	-Fix for PowerShell code in Invoke-PSInject too long #423
	-Fix for agent shell commands #424
	-Fix prompt line wrapping #430
	-Fix screenshot module #435
	-Add PowerUpSQL Modules #437
	-Add module to monitor TCP connections #438
	-Fix DLL stager #449
	-Add VNC Inject #452
	-Add HTTP headers to avoid proxy caching #455
	-Fix hard-coded path in the OSX screenshot module. #465
	-Add a module for wlrmdr.exe popup #472
	-Add a module for SOCKSv5 proxy #478
	-Fix bug in HTTP handler that can throw exceptions while parsing Cookies #479
	-Add a BashBunny HID stager #480
	-Update Inveigh 1.3.1 Modules #483
	-Add support for Arch Linux and rejigged the Unknown distro option #484
	-Fix for issue #420 non-ascii bug #489
	-Fix the listeners API call #490
	-Fix PKCS7 padding to be RFC compliant #492
	-Add custom headers if any #495
	-Fix using netifaces() for getting iface #496
	-Add Session Gopher module
	-Fix for issue 340 Added pip install setuptools and apt-get install libssl-dev


9/23/2016
---------
-Version 2.0.0 beta, DerbyCon release

-Listeners abstracted out to modules
    -Flask used for listener/http instead of base http server
    -client key negotiation abstracted out and implemented in agents

-New nested "routing/metadata" packet structure introduced in prep for additional transports
    -all packetes now wrapped with an HMAC'ed RC4 "routing" packet that uses the staging key
        -this is so all agents can decrypt 'routing' information for future p2p comms 
    -increases flexibilty for malleable comms (i.e. sessionid removed from POST requests)
    -removes the need to keep track of which URIs are used for tasking/post/staging

-Agent data handling improved and abstracted away for listener module use
    -handle_agent_data() handles raw packets, usable by any listener module
        -handle_agent_staging() handles agent key exchange/staging
        -handle_agent_request() handles an agent tasking request
        -handle_agent_response() handles an agent result response

-EmPyre integration:
    -Start of integration of EmPyre staging/comms implemented in listeners/http
    -Agent is language-aware:
        "interact AGENT" drops you into the language-appropriate agent menu
        "usemodule [tab]" from an agent only tab-completes language-appropriate modules
    -stagers were broken out into operating system designations:
        -stagers.generate_launcher() now accepts a language specification, which wraps
            the stager generation functionality for listener module

-PowerShell:
    -RC4 implemented for first stage obfuscation
    -staging now uses HMAC and nonces
    -epoch-syncing removed
    -core agent cleanup

-Listeners:
    added http
    added http_foreign (for 'foreign' Emire listeners)
    added meterpreter (for meterpreter/cobalt strike, using Invoke-Shellcode)
    added management/switch_listener module which switches an agent to a new listener module comms
    redid hop listeners, added listeners/http_hop
    added listeners/http_com which uses IE com objects for communications

-Tons of bug fixes (and new bug introductions :)
-Removed lots of code rot
-Vastly increased debugging output (--debug 2)
-New 'Language'/'MinLanguageVersion' options added to modules
-stagers now have a 'language' option, and are folder-separated by operating system
-added @mattifestation's AMSI bypass into PowerShell stagers 'safe checks'
-redid PowerShell jobs architecture to use a separate app domain instead of PowerShell jobs
-Added key reneogitation in case agents are 'orphaned'
-moved stager.ps1/stager.py to ./agent/stagers/http.ps1 / ./agent/stagers/http.py
-agent generation now patches in the comms methods into the base agent.ps1 (need to do agent.py)
-powershell listeners are now properly hot-swappable with management/switch_listener
-the external/generate_agent module will now generate a staged agent and preregister it (only for PowerShell at this time)
-PowerView code updated
-PowerUp code updated
-new tables -> results and taskings to separate out stuff for the RESTful API 
-CLI/RESTful API broken, needs testing


7/20/2016
---------
-Version 1.5.3
-Fix for issue #273 - added hostnames to raw screenshot output file
-Fix for issue #285 - credential export supporting commas
-Start of code standardization/pep8 cleanup - mods to agents.py, empire.py, and credentials.py
-moved collection/keethief to collection/vaults/keethief
-added collection/vaults/find_keepass_config to enumerate KeePass configs on a system
-added collection/vaults/add_keepass_config_trigger to add a trigger backdoor to all reachable KeePass instances
-added collection/vaults/get_keepass_config_trigger to enumerate all triggers for all reachable KeePass instances
-added collection/vaults/remove_keepass_config_trigger to remove all triggers for all reachable KeePass instances
-Misc. bug fixes

7/16/2016
---------
-Added collection/keethief module to pilfer KeePass key material from memory
-"creds X" now searches additional fields for the term (like domain)
-merged credentials/enum_cred_store from @BeetleChunks

7/15/2016
---------
-Merged @rvrsh3ll's collection/browser_data module
-Merged @curi0usJack's situational_awareness/network/smbautobrute module
-fix for issue #258 - "interact AGENT" now works globally in every menu except an active agent menu
-fix for issue #221 - hop listeners
-fix for issue #252 - management/invoke_script now no longer requires an external script
-fix for issue #257 - sysinfo now executed after running the steal_token command 

6/24/2016
---------
-Updated Invoke-Mimikatz to include a fix for multi-cpu boxes/processor detection
-Merged @n0clues pull request to change paths from %TEMP% to %PUBLIC% for spawnas module to fix a bug when spawning as a different user.
-Fixed a typo in the dcsync_hashdump that caused it to crash the Empire server
-Merged in Inveigh 1.1.1 and current Tater build thanks to @Kevin-Robertson
-Fixed a bug in the REST API due to the port being a string and not an int
-Added 417 Expectation failed error bug fix for older proxies (Squid) thanks to @i223t

6/9/2016
---------
-Updated SQLite dll for Get-ChromeDump.ps1

5/27/2016
---------
-Fixed format issues with Get-ComputerDetails.ps1
-More verbose output added to PowerUp's Invoke-ServiceCMD 
-Made Get-SPN PowerShell 2.0 compatible 
-Updated RunAs to include an argument parameter
-Merged @tristandostaler's /api/map feature to the Rest API
-Merged in @andrew-morris's installer update to include -Y switch for apt-get commands
-Merged in MS16-032 local privesc from @leoloobeek

5/4/2016
---------
-Merged @jaredhaight's Invoke-MetasploitModule module

5/2/2016
---------
-tightened up argparse validation

4/24/2016
---------
-Added credentials/get_spn_tickets to request SPN tickets.
-Added credentials/mimikatz/extract_tickets

4/21/2016
---------
-Merged @Subtee's regsvc32 (sct) stager

4/1/2016
---------
-listener starting now returns more verbose errors on failure in console and API
-merge of @mynameisiv's .jpg screenshot PR
-Fix for path errors in some cases for ./setup/setup_database.py

============
3/31/2015 - RELEASE 1.5
============
-Encompasses all changes since the 1.4 tagged release


3/31/2016
---------
-Merge of Inveigh 1.1 update and privesc/tater
-Updated of Invoke-Mimikatz.ps1 source
-Updated mimikatz dlls to version 2.1 alpha
-Included modification to suppress cmd.exe when spawned via PTH.

3/30/2016
---------
-Added loading of external modules with 'load /path/modules/'

3/25/2016
---------
-RESTful API modifications
-expanded agent/server epoch check to +/- 12 hours
-stagers now run -sta

3/24/2016
---------
-RESTful API modifications

3/22/2016
---------
-added auth to RESTful API, additional API fixes

3/21/2016
---------
-start of RESTful API implementation

3/19/2016
---------
-PowerView.ps1 update and multiple related module additions
-added github issue templates
-added situational_awareness/network/powerview/get_gpo_computer

3/11/2016
---------
-added privesc/getsystem
-bug fix for Invoke-PsExec and some x64 pointers

3/3/2016
---------
-first pass at stager retry interval
-download chunking modified

2/17/2016
---------
- '--debug 2' now displays debug information to the console as well as the empire.debug file
-added privesc/mcafee_sitelist

1/15/2016
---------
-start of command line option integration, use './empire -h' to see options
-bug fixes
-'searchmodule' with no arguments now lists all modules

1/14/2016
---------
-Fix for some UTF-8 encoding issues

1/10/2016
----------
-Corrected several bugs in how the workingHours window is handled in the agent


============
12/29/2015 - RELEASE 1.4
============
-Encompasses all changes since 1.3.1 tagged release


12/29/2015
----------
-Added situational_awareness/network/powerview/find_managed_security_groups to integrate @stufus' new code
-Fixed various issues with agent profile handling
-'DefaultProfile' option in listener menu is now tab-completable and can take a path to a profile.txt

12/28/2015
----------
-Merge of @stufus' Find-ManagedSecurityGroups code into PowerView.ps1 base

12/26/2015
----------
-Merge of @jamcut's situational_awareness/host/findtrusteddocuments module

12/22/2015
----------
-Sync of Kevin Robertson's lateral_movement/inveigh_relay module
-Sync @stufus' exfiltration/egresscheck module
-Added module menu dynamic sizing for prettified output

12/20/2015
----------
-hop.php redirector fix

12/16/2015
----------
-Sync of Kevin Robertson's collection/inveigh update
-Added trollsploit/rick_ascii
-Bug fixes

12/11/2015
----------
-Updated powerview.ps1
-Added situational_awareness/network/powerview/get_cached_rdpconnection
-Added situational_awareness/network/powerview/set_ad_object
-Added management/downgrade_account
-Merge of @mubix's setup automation

12/9/2015
---------
-Added credentials/mimikatz/cache and credentials/mimikatz/sam

11/30/2015
----------
-Combined persistence/debugger/* into persistence/misc/debugger
-Added SysWow64 option to management/spawn to spawn a 32-bit powershell.exe
-Added persistence/userland/backdoor_lnk

11/29/2015
----------
-Built several modules in management/mailraider/* to integrate @xorrior's MailRaider.ps1

11/28/2015
----------
-Merged @xorrior's FoxDump and ChromeDump modules

11/25/2015
----------
-Merged @rvrsh3ll's lateral_movement/invoke_sshcommand

11/24/2015
----------
-Added script autorun functionality

11/23/2015
----------
-Merged @rvrsh3ll's recon/http_login

11/21/2015
----------
-Merge of exploitation/exploit_jboss, bug fix
-Fix in case module returns None
-Merged debian setup.sh fix
-Merged non-interactive cert generation and added to setup.sh
-Fixed nested menu bug that caused buildup of "Agent X not active." 
-Main display menu now shows each time "main" menu is entered

11/8/2015
---------
-All PowerUp modules now dynamically built from a single source file
-PowerUp bug fixes
-Added privesc/powerup/service_exe_restore, pulled logic from other modules
-Added management/spawnas to spawn agents with explicit credentials
-Debug functionality (--debug) now outputs the source of the last tasked script to ./LastTask.ps1
-Write-Verbose and Write-Debug lines now stripped from tasked scripts
-Added situational_awareness/network/powerview/get_forest module

11/4/2015
---------
-Added persistence/misc/add_netuser to add local/domain users

11/2/2015
---------
-Fixed small bug in TASK_CMD_WAIT response parsing


============
10/30/2015 - RELEASE 1.3.1
============
-Updated reflectivepick dlls to fix bug in injection and dll payload injection


============
10/29/2015 - RELEASE 1.3
============
-Encompasses all changes since 1.2 tagged release


10/26/2015
----------
-Fix for psinject bug due to lack of .NET 4.0 on target.
-Fix for bug in persistence/misc/add_sid_history

10/23/15
--------
-Updated powerview.ps1 source to Version 2.0
-Built a way to dynamically generate the stripped PowerView code for functions needed by PowerView modules (helpers -> generate_dynamic_powershell_script), and updated all relevant PowerView modules
-Renamed PowerView modules to better match PowerView 2.0 naming scheme and moved to situational_awareness/network/powerview/*
-Removed old split-out PowerView source files
-Removed situational_awareness/network/netview
-Combined stealth_userhunter into option for userhunter
-Added situational_awareness/network/get_forest_domain, situational_awareness/network/powerview/get_object_acl, situational_awareness/network/powerview/find_computer_field, situational_awareness/network/powerview/find_user_field, situational_awareness/network/powerview/get_ou, situational_awareness/network/powerview/get_group, situational_awareness/network/powerview/get_group_member, situational_awareness/network/powerview/get_gpo, situational_awareness/network/powerview/find_gpo_location, situational_awareness/network/powerview/find_gpo_computer_admin, situational_awareness/network/powerview/process_hunter, situational_awareness/network/powerview/find_foreign_group, situational_awareness/network/powerview/find_foreign_user
-renamed collection/filesearch to collection/find_interesting_file

9/21/2015
---------
-Fix for 'skywalker' file overwrite exploit on control server (thanks @zeroSteiner!)

9/12/2015
---------
-Added credentials/mimikatz/mimitokens to take advantage of Mimikatz' token listing/elevation
-Added management/enable_multi_rdp to patch terminal services to allow mutiple connections
-Fixed bug in write_dllhijacker that prevented the dll from being written out


============
8/30/2015 - RELEASE 1.2
============
-Encompasses all changes below
--- 'Native' shell commands in agent core ported to WMI equivalents
--- HMAC now uses SHA1 instead of MD5
--- Numerous bug fixes and UI tweaks throughout code
--- Six new modules and WAR stager added, /sids option added to golden_ticket
--- Fixed international locale bug with unicode text in agent.ps1


8/29/2015
---------
-HMAC algorithm for packet comms upgraded to use SHA1 instead of MD5
-credentials collected from collection/prompt now scraped/added to credential model

8/26/2015
---------
-Added module privesc/bypassuac_wscript
-Added module collection/inveigh
-Added stager war

8/24/2015
---------
-Added credentials/mimikatz/dcsync for remote DC credential extraction
-Added situational_awareness/network/get_domaintrusts
-Added /sids argument for credentials/mimikatz/golden_ticket
-Added credential parsing for dcsync output
-updated links for PowerTools
-Fixed bug in credential parsing with ":" inside of the password,username, or domain
-Fixed international locale bug with unicode text in agent.ps1. Now all results are base64 encoded prior to being packetized. Encoding will be handled at server.

8/20/2015
---------
-Continued porting native shell commands to WMI replacents in agent core
-In agent menu, 'shell CMD' now runs straight IEX CMD, and 'help agentcmds' shows safe aliases
-Modified ./setup/reset.sh to work from parent or ./setup/ folders
-Agent core functions streamlined
-"list [agents/listeners] <modifier>" should now be a global command

8/19/2015
---------
-Added collection/netripper, port of the NetRipper project
-Added collection/packet_capture for netsh event tracing
-Added management/zipfolder for native folder compression
-Corrected menu behavior on agent exit, bug fix on some dir behavior
-Started porting native shell commands to WMI in the agent core

============
8/16/2015 - RELEASE 1.1
============
-Encompasses all changes below
--- Crypto patch to prevent DOS condition
--- Numerous bug fixes throughout code
--- Extra modules added and HTA stager
--- Ability for agents to die after certain number of failed checkins
--- Added ability to easily remove "stale" agents


8/15/2015
---------
-Added modules management/timestomp, trollsploit/process_killer, persistence/elevated/wmi, situational_awareness/network/smbscanner, lateral_movement/invoke_psexec
-Accepted HTA Stager from subtee

8/12/2015
--------
-Merged in list stale and remove stale functionality
-Fixed delay in list stale feature
-Fixed active agent message in list stale feature
-Fixed registry storage in schtasks and registry persistence modules (userland and elevated)

8/11/2015
---------
-Merged in Lost Agent Detection
-"agents> remove X" now removes agents that checked in > X minutes ago
-"agents> list stale" and "agents> remove stale" now list/remove stale agents past their max checkins

8/10/2015
---------
-Fixed tab completion of usestager module
-Added dependencies for Ubuntu 14.04
-Fixed IP Whitelisting set from file
-Added "Lost Agent Detection". Allows the ability for an agent to die after a certain number of missed checkins. This is implemented via the "lostlimit" command. Default set to 60 missed checkins. 

8/9/2015
----------
-Fixed flaw in crypto allowing a DOS condition. 
-Added authentication to the AES crypto scheme to verify integrity of messages

8/6/2015
-----------
-Initial release. All components released
-Commited path fix to correct bug in certain modules
```
