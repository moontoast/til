#TIL how to restart postgres

##If your machine crashes or gets rebooted improperly, you may need to restart the server.

###Begin by removing any latent .pid files

```
cd /usr/local/var/postgres/
rm *.pid
```

###Then unload the server and reload

```
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```
