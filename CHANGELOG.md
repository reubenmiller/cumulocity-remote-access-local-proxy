
# Releases

## 2.0.0

### Breaking changes

* Renamed command structure and parameter names. Checkout the [migration notes](docs/MIGRATION_V2.md) for full details to get the most out of the newer version.

* Restructured project and dependencies
    * Add code formatting and linting
    * Refactor code to simplify interactions between the local tcp server and the websocket client
    * Add unit and integration tests (coverage currently around ~85%)

* Enabled calling project using just the module name, i.e. `python3 -m c8ylp.main` => `python3 -m c8ylp`

* Added repo hosted cli [documentation](docs/cli/C8YLP.md)

* A PID file is no longer created when using server mode `c8ylp server`. This feature has been removed from c8ylp. It is now recommended that users use the `c8ylp connect ssh` or `c8ylp plugin command` which will automatically shutdown the local proxy after the user is finished with it.

### Features

* Load configuration from an environment via the `--env-file` parameter and support caching the Cumulocity token to it.

* Support usage of random port when starting the local proxy via `--port 0`

* Add interactive ssh connection which starts a once-off local proxy on a random port and then starts an SSH client automatically. Once the ssh client disconnects the local proxy is shutdown.

* [c8ylp plugin command](docs/cli/C8YLP_PLUGIN_COMMAND.md) Generic subcommand to execute custom commands to launch ssh yourself (instead of via `c8ylp connect ssh`). This allows you to customize your ssh options.

* Plugin support to allow the user to extend c8ylp functionality by use of external plugins in the form of python or shell scripts. See [docs/PLUGINS](docs/PLUGINS.md) for information

* Support multiple environment variables for setting Cumulocity credentials to improve compatibility with other Cumulocity tooling

### Bug fixes

* Port timeout error when running on windows

* Fixed randomized port race condition by letting the operating system assign a random port when starting the local tcp server