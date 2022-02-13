# Bypasses

Bypasses are stored in yamls found in `/empire/server/bypass/` and uses a similar formatting as modules. Bypasses are currently only available to PowerShell modules and require a minimum version of PowerShell 3. Earlier version of PowerShell did not contain protections that require bypasses.

When Empire first loads, it will wrie the data from the yamls to the database. The bypasses can then be edited via Starkiller or the API with the changes going only to the version stored in the database.

### Example Bypasses YAML

```
name: ''
authors:
  - ''
description: ''
comments:
  - ''
language: powershell
min_language_version: '3'
script: ''


```
