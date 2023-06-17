# Starkiller
Starkiller is a Frontend for [Powershell Empire](https://github.com/BC-SECURITY/Empire/). It is a web application written in VueJS. If you'd like to contribute please follow the [Contribution guide](/CONTRIBUTING.md). If you'd like to request a feature or report a bug, please follow the [Issue template](/.github/ISSUE_TEMPLATE.md).

# Getting Started
As of Empire 5.0 and Starkiller 2.0, you no longer need to install Starkiller or build it from source.
It is prepackaged in Empire as a submodule and served via Empire's API.

# Sponsorship and extra features
[Sponsoring](https://github.com/sponsors/BC-SECURITY/) at the `Individual` level will give access to extra features.
At the moment, the extra Starkiller sponsorship features include:

  ## Dashboard
  <div align="left"><img width="800" src="https://github.com/BC-SECURITY/Starkiller/assets/9831420/7fda92cd-52ab-4d84-a835-89c35b38cf7e"></div>

  ## Graph View
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/216792129-5b0fed82-b209-48cb-9a43-eeb3e69c7229.gif"></div>

  ## Interactive agent shell
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/104983879-e37fc700-59ca-11eb-9c90-bd2d166c4ac5.gif"></div>
  
  ## Process Browser
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/131264080-0264558d-59c4-44d9-8dae-7b518c47a9cb.gif"></div>

  ## Modify Module Scripts
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/221427395-28d63b1d-bbe5-423e-9113-e58a10a86ced.gif"></div>

  ## Enable/Disable modules
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/123528242-e7f78c80-d69a-11eb-9e88-3410c151cd20.gif"></div>

  ## Proxy Management
  <div align="left"><img width="800" src="https://user-images.githubusercontent.com/9831420/210124448-4f1107b0-3250-4faa-8ea9-4daec77e277e.gif"></div>

There is also a collection of Empire plugins available via sponsorship.

Thanks to our sponsors the following features which started as sponsor features have been moved to the public and kali builds.
- File browser
- Popout windows
- Chat widget
- Bypass management
- Malleable profile management

## Build and run from source
Prerequisites:
* [Node.js](http://nodejs.org/) 16+.
* [Yarn](https://classic.yarnpkg.com/en/docs/install)
Currently it has been tested using Yarn 1.22.
```
yarn
```

### Compile and hot-reload for development
```
yarn dev
```

### Compile and minify for production
```
yarn build
```

## Changelog

Detailed changes for each release are documented in the [changelog](./CHANGELOG.md).
