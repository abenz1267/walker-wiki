# General Config

### General

You can customize how Walker behaves and interacts by adjusting it's configuration to your liking.\
\
Default path for configuration file is `~/.config/walker/config.toml`.

Have a look at the default configuration for a reference: [https://github.com/abenz1267/walker/blob/master/resources/config.toml](https://github.com/abenz1267/walker/blob/master/resources/config.toml)

### Options

| key                       | type    | default   | description                                                                                                          |
| ------------------------- | ------- | --------- | -------------------------------------------------------------------------------------------------------------------- |
| force_keyboard_focus      | boolean | false     | force keyboard focus to stay in walker                                                                               |
| close_when_open           | boolean | true      | invoking walker while it's already open will close it                                                                |
| click_to_close            | boolean | true      | clicking outside of the main walker box will close it                                                                |
| selection_wrap            | boolean | false     | will wrap the selection                                                                                              |
| global_argument_delimiter | string  | `#`       | used to delimit arguments, f.e. `query#arg` means `arg` will be send as an argument to Elephant                      |
| exact_search_prefix       | string  | `'`       | can be used to tell Elephant to use exact search instead of fuzzy search                                             |
| theme                     | string  | `default` | theme to use                                                                                                         |
| disable_mouse             | boolean | false     | disables mouse-interaction with Walker, **except** for drag&drop from preview pane                                   |
| debug                     | boolean | false     | enables debug printing in order to print various info, f.e. available/implemented actions, currently pressed keybind |
| shell.anchor_top          | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_bottom       | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_left         | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_right        | boolean | false     | anchor for window                                                                                                    |

### Placeholders

Placeholders for the input or empty list can be configured as such:

```
[placeholders]
"default" = { input = "Search", list = "No Results" }
"desktopapplications" = { input = "Start", list = "No Application" }
```

### Providers

#### Global Config

| key           | type        | default                                                           | description                                              |
| ------------- | ----------- | ----------------------------------------------------------------- | -------------------------------------------------------- |
| `default`     | string list | `["desktopapplications", "calc", "runner", "menus", "websearch"]` | all providers that should be queried by default          |
| `empty`       | string list | `["desktopapplications"]`                                         | all providers that should be queried when query is empty |
| `max_results` | number      | `50`                                                              | global max amount of results                             |

#### Sets

Walker allows you to configure "sets" that you can launch, overwriting the configuration from above. Example:

```
[providers.sets.omarchy]
default = [
  "menus:omarchy",
  "menus:omarchylearn",
  "menus:omarchytrigger",
  "menus:omarchycapture",
]
empty = ["menus:omarchy"]
```

Running `walker -s omarchy` launches Walker with these specified providers. `default` sets the providers that will be queried, while `empty` defines which ones will display entries, without searching.

#### Prefixes

Prefixes can be used to explicitly target a provider, f.e.

```
[[providers.prefixes]]
prefix = ">"
provider = "runner"
```

will allow you to explicitly query the `runner` provider.

#### Amount of displayed results

You can adjust the amount of displayed results per provider, f.e.

```
[providers.max_results_provider] # define max results per provider in here
desktopapplications = 10
```

will show at most 10 entries for the `desktopapplications` provider.

#### Provider-Specific Configuration

##### Clipboard

| key           | type   | default            | description                 |
| ------------- | ------ | ------------------ | --------------------------- |
| `time_format` | string | `"%d.%m. - %H:%M"` | time format of the sub-text |

### Global Keybinds

The following global keybinds can be configured:

- `close`
- `next`
- `previous`
- `toggle_exact`
- `resume_last_query`
- `quick_activate`

You can define multiple binds per actions, such as:

```
next = ["Down", "ctrl n", "ctrl j"]
```
