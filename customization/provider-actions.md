# Provider Actions

Walker gives you the freedom to provide multiple actions/keybinds for a list item. These are configured in the `[providers.actions]` section of the config. This section will be merged with the default configuration.

```
[providers.actions]
runner = [
  { action = "run", default = true, bind = "Return" },
  { action = "runterminal", label = "run in terminal", bind = "shift Return" },
]
```

There is a bit of magic behavior going on:

- item has only 1 action and no bind set ⇒ automatic fallback
- default `bind` key ⇒ `Return`
- default `after` key ⇒ `Close`
- default `label` key ⇒ `action` key

### Possible `after` keys and their behavior

|                  |                                  |
| ---------------- | -------------------------------- |
| KeepOpen         | Activate item + select next      |
| Close            | Close                            |
| Nothing          | Nothing                          |
| Reload           | Reload with current query        |
| ClearReload      | Clear query and reload           |
| AsyncClearReload | Reload gets triggered by backend |
| AsyncReload      | Reload gets triggered by backend |

### Special actions

|                      |                              |
| -------------------- | ---------------------------- |
| provider:\<provider> | switches to a given provider |
| set:\<set>           | switches to a given set      |
|                      |                              |

### Fallbacks

Often times, you have multiple providers with the same actions, example: `menus:open` is a common action for custom menus. Instead of having to define this action for every provider, Walker allows you to set fallbacks, f.e.:

```
[providers.actions]
fallback = [
  { action = "menus:open", label = "open", after = "Nothing" },
  { action = "erase_history", label = "clear hist", bind = "ctrl h", after = "AsyncReload" },
]
```

You can define your own fallbacks in a similar fashion.
