# Upgrade

For example you have an existing version, say 4.4.

`brew install mongodb-community@5.0`

`mongo`

`db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )`

> { "featureCompatibilityVersion" : { "version" : "4.4" }, "ok" : 1 }

`db.adminCommand( { setFeatureCompatibilityVersion: "5.0" } )`

> { "ok" : 1 }

`db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )`

> { "featureCompatibilityVersion" : { "version" : "5.0" }, "ok" : 1 }

## Errors

`featureCompatibilityVersion`

Installing 6.0 has an issue with a previous version.

```json
{"t":{"$date":"2023-06-12T08:13:13.659+01:00"},"s":"F",  "c":"CONTROL",  "id":20573,   "ctx":"initandlisten","msg":"Wrong mongod version","attr":{"error":"UPGRADE PROBLEM: Found an invalid featureCompatibilityVersion document (ERROR: Location4926900: Invalid featureCompatibilityVersion document in admin.system.version: { _id: \"featureCompatibilityVersion\", version: \"4.4\" }. See https://docs.mongodb.com/master/release-notes/5.0-compatibility/#feature-compatibility. :: caused by :: Invalid feature compatibility version value, expected '5.0' or '5.3' or '6.0. See https://docs.mongodb.com/master/release-notes/5.0-compatibility/#feature-compatibility.). If the current featureCompatibilityVersion is below 5.0, see the documentation on upgrading at https://docs.mongodb.com/master/release-notes/5.0/#upgrade-procedures."}}
```

➜  ~ brew services start mongodb-community
Bootstrap failed: 5: Input/output error
Try re-running the command as root for richer errors.
Error: Failure while executing; `/bin/launchctl bootstrap gui/502 /Users/[USER]/Library/LaunchAgents/homebrew.mxcl.mongodb-community.plist` exited with 5.
