# Client

The Client configuration is managed via [empire/client/config.yaml](https://github.com/BC-SECURITY/Empire/blob/master/empire/client/config.yaml).

*   **servers** - The servers block is meant to give the user the ability to set up frequently used Empire servers.

    If a server is listed in this block then when connecting to the server they need only type: `connect -c localhost`.

    This tells the client to use the connection info for the server named localhost from the yaml. In addition, if autoconnect is set to `true`, the client will automatically connect to that server when starting up.

    ```yaml
    servers:
    localhost:
      host: https://localhost
      port: 1337
      socketport: 5000
      username: empireadmin
      password: password123
      autoconnect: true
    ```
* **suppress-self-cert-warning** - Suppress the HTTP warnings when connecting to an Empire instance that uses a self-signed cert.
* **auto-copy-stager** - Automatically copy generated stager text to the clipboard.
* **shortcuts** - Shortcuts defined here allow the user to define their own frequently used modules and assign a command to them.

Let's look at 3 distinct examples. All of which can be found in the default [config.yaml](https://github.com/BC-SECURITY/Empire/blob/master/empire/client/config.yaml)

```yaml
shortcuts:
powershell:
  sherlock:
    module: powershell/privesc/sherlock
```

This first example is the simplest example. It adds a `sherlock` command to the Interact menu for Powershell agents. It does not pass any specific parameters.

```yaml
shortcuts:
  powershell:
    keylog:
      module: powershell/collection/keylogger
      params:
        - name: Sleep
          value: 1
```

This next one is slightly more complex in that we are telling the shortcut to set the _Sleep_ parameter to 1. Note that if there are any other parameters for this module that we don't define, it will use whatever the default value is.

```yaml
shortcuts:
  powershell:
    bypassuac:
      module: powershell/privesc/bypassuac_eventvwr
      params:
        - name: Listener
          dynamic: true
```

This third one gets a bit more complex. Instead of providing a `value` to the parameter, it is marked as `dynamic`. This tells the CLI that it expects the user to send the parameters as part of their command. In other words, the user needs to type `bypassuac http1` in order for this to execute. The parameters are passed in the order they are defined in config.yaml. There are some convenient autocompletes if the field is named `Listener` or `Agent`.

```yaml
shortcuts:
  powershell:
    whoami:
      shell: whoami
```

The last one is much more simple. Instead of running a module, we run a shell command.

*   **resource-file** - A resource file is simply a text file with a list of commands to run in order.

    An example txt is shown below yaml

```yaml
resource-file: commands.txt
```

```yaml
# commands.txt
listeners
userlistener
http
set
Port
999
execute
```

* **directories** - Are customized directories for storing directing Empire to read and write from. The defaults for these directories should not have to be updated unless storing writeable files, separately from the server.

```
directories:
  downloads: empire/client/downloads/
  generated-stagers: empire/client/generated-stagers/
```

* **auto-copy-stagers** - Enable stagers to be automatically copied to the client's clipboard.&#x20;
