

Make sure your _/etc/monit.conf_ file imports from this directory:

```
# Include all files from /etc/monit.d/
include /etc/monit.d/*
```

Requires a tiny bit of modification depending on Linux flavor.

## Groups

```
# Simple resource monitoring
# --------
# You may globally manage these from the command line without affecting
# other monitoring with the following command...
# "monit -g resources [stop|start|restart]"

# check against RAM and RAM + SWAP.
check system Memory
        alert root@localhost on { resource } with reminder on 10 cycles
        group resources
        if memory usage > 80% for 5 cycles then alert
                else if passed within 5 cycles then alert
        if loadavg (15min) is greater than 0.95 for 2 cycles then alert
                else if passed within 5 cycles then alert

# check against disk usage
check device Root-filesystem with path /dev/xvda1
        alert root@localhost on { resource } with reminder on 10 cycles
        group resources
        if space usage is greater than 95% for 5 cycles then alert
                else if passed within 5 cycles then alert
```
