# Theme

### General

Walker is built using of \[GTK4]\([https://docs.gtk.org/gtk4/](https://docs.gtk.org/gtk4/)).\
\
Refer to the \[GTK4 Documentation]\([https://docs.gtk.org/gtk4/](https://docs.gtk.org/gtk4/)) for specific information.

### Themes

Themes are built out of the following building-blocks:

* `style.css`
* `layout.xml`    &#x20;
* `keybind.xml`
* `preview.xml`
* `item_<provider>.xml`

\
You don't have to create every file if you want to create a custom theme, only the ones you want to change.\
\
These files should be placed in `~/.config/walker/themes/<THEME>`\


To set the general theme for Walker, change `theme = "<THEME>"` in your `config.toml`.\
\
You can tell Walker to use a different theme, by providing the `-t/--theme` flag.

### Reference

Have a look at the default theme: [https://github.com/abenz1267/walker/tree/master/resources/themes/default](https://github.com/abenz1267/walker/tree/master/resources/themes/default)
