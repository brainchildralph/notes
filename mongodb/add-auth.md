
Without Auth
------

```
mongod
```

Create Administrator
------
```
mongo admin  --eval '
db.createUser(
  {
    user: "admin",
    pwd: "admin",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
  }
)
'
```
等同於：
```
use admin
db.createUser(
  {
    user: "myUserAdmin",
    pwd: "abc123",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
  }
)
```

刪除Admin
```
mongo admin  --eval '
db.createUser( db.dropUser("myUserAdmin")
'
```


With Auth and Port
--------

```
mongod --auth --port 27017
```

