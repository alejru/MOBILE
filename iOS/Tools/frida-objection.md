# FRIDA - OBJECTION
### Environment
We can get BundlePath, CachesDirectory, DocumentDirectory, LibraryDirectory
`# env`

### SQLite connection
```
# sqlite connect CastFrameworkDB.sqlite
SQLite @ CastFrameworkDB.sqlite > .tables
SQLite @ CastFrameworkDB.sqlite > select * from Z_PRIMARYKEY 
```

### Binary Cookies
`# ios cookies get --json`

### Pasteboard Monitor
`# ios pasteboard monitor`

### Reading plist Files
`# ios plist cat userInfo.plist`
