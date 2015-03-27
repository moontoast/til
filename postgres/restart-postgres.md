## How to (Re)start Postgres After an Ungraceful Reboot

If your machine crashes or doesn't get rebooted gracefully, you may experience problems with Postgres when the system comes back up. If Postgres won't start (or you can't connect to it), start by looking for any straggling `.pid` files:

_Note: these instructions assume you're running a homebrew-installed version of Postgres on OS X_

```sh 
cd /usr/local/var/postgres/
rm *.pid
```

Then use `launchd` to restart the Postgres service:

```sh
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```
