# Empire 5 Migration

Empire 5 made some changes to git submodules. Update them.

```
git submodule update --init --recursive
```

You will want to run the install script to get the latest OS dependencies. It has been tested and runs properly on Ubuntu 20.04, Debian 10, and Kali Rolling release.

```
cd setup
./install.sh
```
