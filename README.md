These files go in your _/etc/monit.d/_ directory.

Make sure your _/etc/monit.conf_ file imports from this directory:

```
# Include all files from /etc/monit.d/
include /etc/monit.d/*
```

Requires a tiny bit of modification depending on Linux flavor.
