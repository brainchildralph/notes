#### EOF Changed to "EOF"

**`cat << EOF` -> `cat << "EOF"`**


Without `"`

```
cat << EOF | sed -e 's/^/  /'
adminAuth: {
    type: "credentials",
    users: [{
        username: "admin",                                                              
        password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.",   
        permissions: "*"
    }]
}
EOF
```

Result: 

```
  adminAuth: {
      type: "credentials",
      users: [{
          username: "admin",
          password: "abash8.",
          permissions: "*"
      }]
  }

```

With `"`

```
cat << "EOF"
adminAuth: {
    type: "credentials",
    users: [{
        username: "admin",
        password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.", 
        permissions: "*"
    }]                  
}     
EOF
```

Result: 

```
adminAuth: {
    type: "credentials",
    users: [{
        username: "admin",
        password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.",
        permissions: "*"
    }]
}
```
