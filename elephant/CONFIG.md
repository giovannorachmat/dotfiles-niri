# Elephant
A service providing various datasources which can be triggered to perform actions.

Run `elephant -h` to get an overview of the available commandline flags and actions.
## Elephant Configuration
`~/.config/elephant/elephant.toml`
#### ElephantConfig
| Field | Type | Default | Description |
| --- | ---- | ---- | --- |
|auto_detect_launch_prefix|bool|true|automatically detects uwsm, app2unit or systemd-run|
|launch_prefix|string||overrides the default app2unit or uwsm prefix, if set.|
|overload_local_env|bool|false|overloads the local env|
|ignored_providers|[]string|<empty>|providers to ignore|
|git_on_demand|bool|true|sets up git repositories on first query instead of on start|
|before_load|[]common.Command||commands to run before starting to load the providers|
#### Command
| Field | Type | Default | Description |
| --- | ---- | ---- | --- |
|must_succeed|bool|false|will try running this command until it completes successfully|
|command|string||command to execute|


## Provider Configuration
### Elephant Desktop Applications

Run installed desktop applications.

#### Features

- history
- pin items
- alias items
- auto-detect `uwsm`/`app2unit`


`~/.config/elephant/desktopapplications.toml`
#### Config
| Field | Type | Default | Description |
| --- | ---- | ---- | --- |
|icon|string|depends on provider|icon for provider|
|name_pretty|string|depends on provider|displayed name for the provider|
|min_score|int32|depends on provider|minimum score for items to be displayed|
|hide_from_providerlist|bool|false|hides a provider from the providerlist provider. provider provider.|
|locale|string||to override systems locale|
|action_min_score|int|20|min score for actions to be shown|
|show_actions|bool|false|include application actions, f.e. 'New Private Window' for Firefox|
|show_generic|bool|true|include generic info when show_actions is true|
|show_actions_without_query|bool|false|show application actions, if the search query is empty|
|history|bool|true|make use of history for sorting|
|history_when_empty|bool|false|consider history when query is empty|
|only_search_title|bool|false|ignore keywords, comments etc from desktop file when searching|
|icon_placeholder|string|applications-other|placeholder icon for apps without icon|
|aliases|map[string]string||setup aliases for applications. Matched aliases will always be placed on top of the list. Example: 'ffp' => '<identifier>'. Check elephant log output when activating an item to get its identifier.|
|blacklist|[]string|<empty>|blacklist desktop files from being parsed. Regexp.|
|window_integration|bool|false|will enable window integration, meaning focusing an open app instead of opening a new instance|
|ignore_pin_with_window|bool|true|will ignore pinned apps that have an opened window|
|window_integration_ignore_actions|bool|true|will ignore the window integration for actions|
|wm_integration|bool|false|Moves apps to the workspace where they were launched at automatically. Currently Niri only.|
|score_open_windows|bool|true|Apps that have open windows, get their score halved. Requires window_integration.|
|single_instance_apps|[]string|["discord"]|application IDs that don't ever spawn a new window. |

### Elephant Providerlist

Lists all installed providers and configured menus.


`~/.config/elephant/providerlist.toml`
#### Config
| Field | Type | Default | Description |
| --- | ---- | ---- | --- |
|icon|string|depends on provider|icon for provider|
|name_pretty|string|depends on provider|displayed name for the provider|
|min_score|int32|depends on provider|minimum score for items to be displayed|
|hide_from_providerlist|bool|false|hides a provider from the providerlist provider. provider provider.|
|hidden|[]string|<empty>|hidden providers|

