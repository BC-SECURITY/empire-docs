# Plugin Development

## Using the database
If objects are being retrieved from the database, the service functions require a database session be passed in.
Effectively, this means that you must handle your database session in the plugin. Using the Context Manager syntax
ensures the db session gets cleaned up when done.

```python
from empire.server.core.db.base import SessionLocal

with SessionLocal() as db:
  agents = self.main_menu.agentsv2.get_all(db)
  ...
```

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
* plugin tasks -
  Have plugin tasks where a user might want to come back to see the output at a later time. For this we could have tasks that work in a similar way to agent tasks.
* endpoint for installing plugins -
  A user would be able to provide the URL to a git repository and Empire would download and install the plugin.
