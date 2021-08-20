# Starkiller

![](https://github.com/BC-SECURITY/Starkiller/raw/master/src/assets/icon.png)

## Starkiller

Starkiller is a Frontend for [Powershell Empire](https://github.com/BC-SECURITY/Empire/). It is an Electron application written in VueJS. If you'd like to contribute please follow the [Contribution guide](/CONTRIBUTING.md). If you'd like to request a feature or report a bug, please follow the [Issue template](/.github/ISSUE_TEMPLATE.md).

## Getting Started

* To run Starkiller, you can download the installers for Mac, Linux, and Windows on the [Releases](https://github.com/BC-SECURITY/Starkiller/releases) page.
  * For Mac and Windows - run the installer how you would any other .exe or .dmg
  * For Linux - Change the permissions `chmod a+x starkiller-<version>.AppImage`, then execute `./starkiller-<version>.AppImage --no-sandbox`
* Starkiller is also available via `apt install starkiller` on [Kali](https://www.kali.org/). Kali releases are 30 days ahead of the public release.
* If you want to build from source or run in development mode, instructions are below.

### Build and run from source

Prerequisites:

* [Node.js](http://nodejs.org/) 10+.
* [Yarn](https://classic.yarnpkg.com/en/docs/install)

  Currently it has been tested using Yarn 1.22.0.

  ```text
  yarn install
  ```

#### Compile and hot-reload for development

```text
yarn electron:serve
```

#### Compile and minify for production

```text
yarn electron:build

# Or to target a specific OS.
yarn electron:build:lin
yarn electron:build:win
yarn electron:build:mac
```

Starkiller's build tool, [electron-builder](https://www.electron.build), is not meant to target multiple platforms in a single build. It is also recommended to compile on your target platform. For example, to build for amd64 \(on an amd64 machine\) with an AppImage, the command would be:

```text
yarn electron:build --arm64 --linux AppImage
```

**Note:** To regenerate the icons

```text
npm install -g electron-icon-builder
yarn electron:generate-icons
```

### Compatability Table

Starkiller’s new features occasionally depend on new functionality within Empire. Therefore, it is recommended that you follow this release table for syncing up your Starkiller and Empire versions. If you are using an older version of Empire, Starkiller will warn you when logging in, but will allow you to continue. If there is a new minimum version of Empire required to get all the features out of Starkiller, we will do a minor version bump to Starkiller.

| Starkiller Release | Minimum Empire Version | Notes |
| :--- | :--- | :--- |
| 1.0.x | 3.1.1 | 3.1.1 is the first version of Empire to include all the user endpoints necessary for Starkiller to function |
| 1.1.x | 3.1.5 | 3.1.5 updated the reporting endpoint to have the same result as running it in the CLI. Starkiller 1.1.x uses that reporting endpoint for the reporting tab |
| 1.2.x | 3.2.0 | 3.2.0 added an endpoint for users that is needed for the UI updates introduced in Starkiller 1.2.0 |
| 1.3.x | 3.3.0 | 3.3.0 categorized all of the modules in Empire with corresponding [MITRE techniques](https://attack.mitre.org/techniques/enterprise/) |
| 1.4.x | 3.5.0 | 3.5.0 added real-time notifications for new listeners and agents |
| 1.5.x | 3.6.2 | 3.6.2 added the chat server |
| 1.6.x, 1.7.x | 3.7.0 | 1.6.0 was tested against Empire 3.7.0. There _shouldn't_ be any breaking changes, but there were a lot of code changes. |
| 1.8.x | 4.0.0 |  |

### Changelog

Detailed changes for each release are documented in the [release notes](https://github.com/bc-security/starkiller/releases).

