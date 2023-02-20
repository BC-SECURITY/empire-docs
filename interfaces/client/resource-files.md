# Resource Files

Resource files are a way to script commands for the Empire Client. They are text files that have a newline delimited file of client commands.

To execute a resource file, supply it as a command line parameter. For example `./ps-empire client --resource resource_file.txt`

On startup, the client will execute the lines from the resource file in the order they appear.

Beginning in Empire 4.7.0, resource files can be executed from the client while it is already running by using the `resource` command.

