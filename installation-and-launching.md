# Installation and Launching

### Installing

To install Walker, you must also install the elephant package, as well as any providers you want to be displayed on the menu.

#### Arch

```
yay -S walker
# This will install just the front-end walker package. This will not be functional by inself.
# For example, to install elephant and the apps provider:
yay -S elephant elephant-desktopapplications
# This will install the basic app launcher setup.
```

#### Fedora

```
sudo dnf copr enable errornointernet/walker
sudo dnf install walker
sudo dnf install elephant
```

#### openSuse Tumbleweed

```
# Dependencies
sudo zypper install git cargo gtk4-devel gtk4-layer-shell-devel libpoppler-glib-devel protobuf-devel cairo-devel go make

# Walker
git clone https://github.com/abenz1267/walker.git ~/Downloads/walker
cd ~/Downloads/walker
sudo make install

# Elephant
git clone https://github.com/abenz1267/elephant ~/Downloads/elephant
cd ~/Downloads/elephant
sudo make install

# Provider desktopapplications
cd ~/Downloads/elephant/internal/providers/desktopapplications
sudo make install

# Provider menus
cd ~/Downloads/elephant/internal/providers/menus
sudo make install

# Provider files
cd ~/Downloads/elephant/internal/providers/files
sudo make install
```

### Launching

Elephant has to be running in order for Walker to function.

Starting Elephant is best done as a user-service: you can use `elephant service enable` to generate a systemd user-level service. It will install and enable it, but won't start it. `systemctl --user start elephant.service` in order to start it without rebooting.\
\
When Elephant is running, you can simply launch Walker with `walker`! Done.&#x20;

### Optimizing startup time

Since Walker is based on GTK4, it is by nature slow to startup. A lot of things have to be done each time you open it ⇒ slow.\
\
This can be optimized, by keeping a Walker instance running with `walker --gapplication-service` \
\
This way everything required in order to launch Walker (parsing config, setting up UI etc) is only done once.\
\
Furthermore, you can make Walker popup via a socket call, f.e. `nc -U /run/user/1000/walker/walker.sock` . This is further improve the time till Walker appears on your screen, by avoiding any GTK4 cmdline parsing. So this can be used as a faster alternative to simply calling `walker`.
