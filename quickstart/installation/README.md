# Installation

We recommend the use of [Kali](https://www.kali.org/downloads/), [Poetry](https://python-poetry.org/docs/), or our [Docker images](https://hub.docker.com/r/bcsecurity/empire) to run Empire. Kali Linux users and [Direct Sponsors](https://github.com/sponsors/BC-SECURITY) will receive 30-day early access to new Empire and Starkiller features.

The following operating systems have been tested for Empire compatibility. We will be unable to provide support for other OSs at this time. Consider using our Prebuilt Docker containers which can run on any system.

* Kali Linux Rolling
* Ubuntu 20.04 / 22.04
* Debian 10 / 11
* ParrotOS

As of Empire 4.0, Python 3.8 is the minimum Python version required.

## Github

Note: The `main` branch is a reflection of the latest changes and may not always be stable. After cloning the repo, you can checkout the latest stable release by running the `setup/checkout-latest-tag.sh` script.

```bash
git clone --recursive https://github.com/BC-SECURITY/Empire.git
cd Empire
./setup/checkout-latest-tag.sh
sudo ./setup/install.sh
```

**Sponsors:**

```
git clone --recursive https://github.com/BC-SECURITY/Empire-Sponsors.git
cd Empire-Sponsors
./setup/checkout-latest-tag.sh sponsors
sudo ./setup/install.sh
```

If you are using the sponsors version of Empire, it will pull the sponsors version of Starkiller.
Because these are private repositories, you need to have ssh credentials configured for GitHub. Instructions can be found [here](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh).

## Kali

You can install the latest version of Empire by running the following:

```bash
sudo apt install powershell-empire
```

**Note:** Kali requires you to run Empire with `sudo`.

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
