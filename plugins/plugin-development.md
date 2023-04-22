# Plugin Development


## Execute Function
The execute function is the entry point for the plugin. It is called when the plugin is executed via the CLI or the API. The execute function is passed the following arguments:

* command - A dict of the command arguments, already parsed and validated by the core Empire code
* kwargs - Additional arguments that may be passed in by the core Empire code. Right now there are only two.
  * user - The user database object for the user that is executing the plugin
  * db - The database session object

If the plugin doesn't have `**kwargs`, then no kwargs will be sent. This is to ensure backwards compatibility with plugin pre-5.2.


```python
def execute(self, command, **kwargs):
    user = kwargs.get('user', None)
    db = kwargs.get('db', None)

    return "Execution complete"
```


## Using the database
If objects are being retrieved from the database, the service functions require a database session be passed in.
Effectively, this means that you must handle your database session in the plugin. Using the Context Manager syntax
ensures the db session gets cleaned up when done.

```python
from empire.server.core.db.base import SessionLocal

def execute(self, command, **kwargs):
    user = kwargs.get('user', None)
    db = kwargs.get('db', None)

    agents = self.main_menu.agentsv2.get_all(db)

    return "Execution complete"
```

## Plugin Tasks
Plugins can now store tasks. The data model looks pretty close to Agent tasks. This is for agent executions that:

1. Want to attach a file result
2. Need to display a lot of output, where notifications don't quite work
3. Has output you'll want to look back at later

```python
from empire.server.core.db import models

def execute(self, command, **kwargs):
    user = kwargs.get('user', None)
    db = kwargs.get('db', None)

    input = 'Example plugin execution.'

    plugin_task = models.PluginTask(
      plugin_id=self.info["Name"],
      input=input,
      input_full=input,
      user_id=user.id,
      status=models.PluginTaskStatus.completed,
    )

    db.add(plugin_task)
    db.commit()
```


For an example of using plugin tasks and attaching files, see the [basic_reporting plugin](https://github.com/BC-SECURITY/Empire/blob/main/server/plugins/basic_reporting/basic_reporting.plugin).

## Event-based functionality (hooks and filters)
This is outlined in [Hooks and Filters](./hooks-and-filters.md).

## 4->5 Changes
Not a lot has changed for plugins in Empire 5.0. We've just added a few guard rails for better
stability between Empire versions.

The plugin interface is a guarantee that certain functionality will not be changed outside of major
Empire version updates (ie 4->5). So which functions are guaranteed? Any of the functions on the
`core/*_service` classes not prefixed with a `_`.

Does this mean you can't use `util` functions or modify state in other parts of the empire code?
No. In most cases you will be fine to do so. We as maintainers just can't keep track of any and
every thing a plugin may be doing and guarantee that it won't break in a minor/patch update.
This is no different than the way things were pre 5.0.

* Make sure `self.info` is a dict and not a tuple. A lot of plugins had a trailing comma that caused it to be interpreted as a tuple.
* Update `Author` to `Authors` and follow the new format (Link, Handle, Name)
* The execute plugin endpoint no longer automatically changes the state of the `self.options` dict inside the plugin. Instead, it sends validated parameters to the plugin as a dict and the plugin itself should decide whether it makes sense to modify the internal state or not.
* `plugin_socketio_message` was moved from `MainMenu` to `plugin_service`.
* Example conversion for a 5.0 plugin can be seen in [ChiselServer-Plugin](https://github.com/BC-SECURITY/ChiselServer-Plugin/compare/5.0)


## Future Work
* improved plugin logging -
  Give plugins indidual log files like listeners have. Make those logs accessible via Starkiller.
* endpoint for installing plugins -
  A user would be able to provide the URL to a git repository and Empire would download and install the plugin.
