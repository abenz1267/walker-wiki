# General Config

### General

You can customize how Walker behaves and interacts by adjusting it's configuration to your liking.\
\
Have a look at the default configuration for a reference: [https://github.com/abenz1267/walker/blob/master/resources/config.toml](https://github.com/abenz1267/walker/blob/master/resources/config.toml)



### \[providers.sets]

Walker allows you to configure "sets" that you can launch. Example:

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
