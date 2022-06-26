# Installation

We recommend the use of [Kali](https://www.kali.org/downloads/), [Poetry](https://python-poetry.org/docs/), or our [Docker images](https://hub.docker.com/r/bcsecurity/empire) to run Empire. Kali Linux users and [Direct Sponsors](https://github.com/sponsors/BC-SECURITY) will receive 30-day early access to new Empire and Starkiller features.

The following operating systems have been tested for Empire compatibility. We will be unable to provide support for other OSs at this time. Consider using our Prebuilt Docker containers which can run on any system.

* Kali Linux Rolling
* Ubuntu 20.04
* Debian 10

As of Empire 4.0, Python 3.8 is the minimum Python version required.

## Kali

You can install the latest version of Empire by running the following:

```bash
sudo apt install powershell-empire
```

**Note:** Newer versions of Kali require you to run `sudo` before starting Empire.

## Github

Poetry is a dependency and virtual environment management tool. This is highly recommended if using the SocketIO notification feature introduced in 3.5.0. To install Poetry, please follow the installation guide in the documentation or run `sudo pip3 install poetry`.

To install and run:

```bash
git clone --recursive https://github.com/BC-SECURITY/Empire.git
cd Empire
sudo ./setup/install.sh
```

### Common Issues

Empire still has a few issues installing on Python 3.10. We recommend Python 3.8 or Python 3.9.

#### cffi fails to install via pip/poetry

**Output**

```
  • Installing cffi (1.14.5): Failed

  EnvCommandError

  Command ['/root/.cache/pypoetry/virtualenvs/empire-bc-security-fork-QbDnA-QX-py3.10/bin/pip', 'install', '--no-deps', '/root/.cache/pypoetry/artifacts/d0/e3/60/58172107607ad40fd710df22e324a3ee48174e11f9e228acdaa720f6d1/cffi-1.14.5.tar.gz'] errored with the following return code 1, and output:
  Processing /root/.cache/pypoetry/artifacts/d0/e3/60/58172107607ad40fd710df22e324a3ee48174e11f9e228acdaa720f6d1/cffi-1.14.5.tar.gz
    Preparing metadata (setup.py): started
    Preparing metadata (setup.py): finished with status 'done'
  Building wheels for collected packages: cffi
    Building wheel for cffi (setup.py): started
    Building wheel for cffi (setup.py): finished with status 'error'
    error: subprocess-exited-with-error

    × python setup.py bdist_wheel did not run successfully.
    │ exit code: 1
```

This has been found to occur when using Python 3.10. Install Python 3.9, switch the poetry env to use it, then rerun the install.

**Solution**

```
# If 3.9 isn't available via apt, install it manually or via pyenv
apt install python3.9 python3.9-dev
poetry env use $(which python3.9)
setup/install.sh
```

#### ModuleNotFoundError: No module named '\_tkinter'&#x20;

In Empire 4.7.0 this has been updated to be non-fatal. The error will show up as `[!] Failed to load tkinter. Please install tkinter to use the file prompts.`\
\
[tkinter](https://docs.python.org/3/library/tkinter.html) is a GUI tool built into python itself. It is possible for some distributions of Python to exclude it.

tkinter is only used in the Empire client when using the `-p` option to prompt a file selection on certain commands. For this reason, its not a critical dependency. In Empire 4.7, we made the inclusion of `tkinter` optional.

**Solution**

There is no single way to fix this problem, because it depends on how your Python was installed. It has been reported that a variation of the following apt commands will add tkinter to the right place. The command you use would depend on how your python version was installed to begin with. For example, if your Python lives in `/usr/local/lib/python3.8/`, you’d want to use `apt install python3.8-tk`.

```
apt install python3-tk
apt install python3.8-tk
```

## Docker

If you want to run Empire using a pre-built docker container.

**Note**: For size savings on the image, it is not pre-built with the libraries needed for jar, dmg, and nim stagers. To add these to your image, run the `install.sh` script in the container and answer `y` to the prompts.

```bash
# Pull the latest image
docker pull bcsecurity/empire:latest

# Run the server with the rest api and socket ports open
docker run -it -p 1337:1337 -p 5000:5000 bcsecurity/empire:latest

# Run the client
docker run -it -p 1337:1337 -p 5000:5000 bcsecurity/empire:latest client

# To run the client against the already running server container
docker container ls
docker exec -it {container-id} ./ps-empire client

# with persistent storage
docker pull bcsecurity/empire:latest
docker create -v /empire --name data bcsecurity/empire:latest
docker run -it -p 1337:1337 -p 5000:5000 --volumes-from data bcsecurity/empire:latest

# if you prefer to be dropped into bash instead of directly into empire
docker run -it -p 1337:1337 -p 5000:5000 --volumes-from data --entrypoint /bin/bash bcsecurity/empire:latest
```

Note: These are example basic commands to get started with docker. Depending on the use case of the individual, one may need to reference the [Docker documentation](https://docs.docker.com).

All image versions can be found at: [https://hub.docker.com/r/bcsecurity/empire/](https://hub.docker.com/r/bcsecurity/empire/)

* The last commit from master will be deployed to the `latest` tag
* The last commit from the dev branch will be deployed to the `dev` tag
* All GitHub tagged releases will be deployed using their version numbers (v3.0.0, v3.1.0, etc)

## Community-Supported Operating Systems

At this time, we are choosing to only support Kali, Debian 10, and Ubuntu 20.04 installations, however, we will accept pull requests that fix issues or provide installation scripts specific to other operating systems to this wiki.
