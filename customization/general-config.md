# General Config

### General

You can customize how Walker behaves and interacts by adjusting it's configuration to your liking.\
\
Default path for configuration file is `~/.config/walker/config.toml`.

Have a look at the default configuration for a reference: [https://github.com/abenz1267/walker/blob/master/resources/config.toml](https://github.com/abenz1267/walker/blob/master/resources/config.toml)

### Options

| key                       | type    | default   | description                                                                                                          |
| ------------------------- | ------- | --------- | -------------------------------------------------------------------------------------------------------------------- |
| as_window                 | boolean | false     | launch walker as a regular window instead of layer shell application                                                 |
| force_keyboard_focus      | boolean | false     | force keyboard focus to stay in walker                                                                               |
| close_when_open           | boolean | true      | invoking walker while it's already open will close it                                                                |
| click_to_close            | boolean | true      | clicking outside of the main walker box will close it                                                                |
| selection_wrap            | boolean | false     | will wrap the selection                                                                                              |
| global_argument_delimiter | string  | `#`       | used to delimit arguments, f.e. `query#arg` means `arg` will be send as an argument to Elephant                      |
| exact_search_prefix       | string  | `'`       | can be used to tell Elephant to use exact search instead of fuzzy search                                             |
| theme                     | string  | `default` | theme to use                                                                                                         |
| disable_mouse             | boolean | false     | disables mouse-interaction with Walker, **except** for drag&drop from preview pane                                   |
| hide_quick_activation     | boolean | false     | hide the quick activation hints globally                                                                             |
| hide_action_hints         | boolean | false     | hide the actions keybind hints                                                                                       |
| hide_return_action        | boolean | false     | hide actions that are bound to Return                                                                                |
| page_jump_items           | number  | 10        | number of items to skip with Page Up/Down                                                                            |
| single_click_activation   | boolean | true      | activate items with a single click                                                                                   |
| debug                     | boolean | false     | enables debug printing in order to print various info, f.e. available/implemented actions, currently pressed keybind |
| resume_last_query         | boolean | false     | open walker with the last query in place                                                                             |
| actions_as_menu           | boolean | false     | show actions in a menu                                                                                               |
| autoplay_videos           | boolean | false     | auto-play video previews                                                                                             |
| shell.layer               | string  | "overlay" | layershell layer                                                                                                     |
| shell.anchor_top          | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_bottom       | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_left         | boolean | false     | anchor for window                                                                                                    |
| shell.anchor_right        | boolean | false     | anchor for window                                                                                                    |

### List Columns

You can define how many columns the list for specific providers has without creating a new theme. F.e.

```toml
[columns]
"symbols" = 3
```

### Placeholders

Placeholders for the input or empty list can be configured as such:

```
[placeholders]
"default" = { input = "Search", list = "No Results" }
"desktopapplications" = { input = "Start", list = "No Application" }
```

If the input placeholder is prefixed with `cmd:`, it will run the command and use the output as the placeholder.

### Providers

#### Global Config

| key                  | type                            | default                                                           | description                                                                                     |
| -------------------- | ------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `default`            | string list                     | `["desktopapplications", "calc", "runner", "menus", "websearch"]` | all providers that should be queried by default                                                 |
| `empty`              | string list                     | `["desktopapplications"]`                                         | all providers that should be queried when query is empty                                        |
| `ignore_preview`     | string list                     | `[]`                                                              | all providers that should not display a preview.                                                |
| `max_results`        | number                          | `50`                                                              | global max amount of results                                                                    |
| `argument_delimiter` | map, key: string, value: string | ``                                                                | used to delimit arguments, f.e. `query#arg` means `arg` will be send as an argument to Elephant |

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

#### Emergency Mode

Walker allows you to define static "emergency entries" in case Elephant isn't connected. Example:

```toml
[[emergencies]]
text = "Firefox"
command = "firefox-developer-edition"

[[emergencies]]
text = "uuctl"
command = "uuctl"
```

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
- `left`
- `right`
- `up`
- `down`
- `previous`
- `toggle_exact`
- `resume_last_query`
- `quick_activate`

You can define multiple binds per actions, such as:

```
next = ["Down", "ctrl n", "ctrl j"]
```
