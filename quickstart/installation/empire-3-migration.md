# Empire 3 Migration

Empire 4 made some changes to the crypto libraries. Run these commands to refresh your virtual environment, if you already have one.

```
poetry run python -m pip uninstall PyCrypto
poetry run python -m pip uninstall pycryptodome
```

You will want to run the install script to get the latest OS dependencies. It has been tested and runs properly on Ubuntu 20.04, Debian 10, and Kali Rolling release. When prompted for dotnet, type `y` to get the required dependencies for C# agents.

```
cd setup
./install.sh
```
