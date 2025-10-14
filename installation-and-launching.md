# Installation and Launching

### Arch

```
yay -S walker
```

Will install a basic OOTB Walker+Elephant setup.\
\
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
