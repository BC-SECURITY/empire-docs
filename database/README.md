# Database

Beginning in Empire 5.0, MySQL is the default database. Trying to support multi-user setups and expanding our usage of the database started to reach limitations in SQLite. SQLite is still supported, and we run the full test suite against it, but is not recommended.

For database configuration see the [Configuration](../configuration/server.md) section.

## Setup
The install script will install MySQL if you install on one of the supported operating systems. If you want to switch between MySQL and SQLite, change the `use` property in the `database` section of the configuration file.

There is an environment variable `DATABASE_USE` that can be used to overwrite the `database.use` property in `config.yaml`.

# Docker
The Docker image still defaults to SQLite. To use MySQL, you can change `config.yaml` or utilize the `DATABASE_USE` enviornment variable. For example `docker run -p 3306:3306 -p 1337:1337 -e DATABASE_USE='mysql' -it bcsecurity/empire:latest`.
The Docker image does not contain MySQL, so you will need to run a MySQL container or install MySQL on the host machine.
