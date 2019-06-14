#### EOF Changed to "EOF"

**`cat << EOF` -> `cat << "EOF"`**

       No  parameter  and variable expansion, command substitution, arithmetic
       expansion, or pathname expansion is performed on word.  If any  charac‐
       ters  in  word are quoted, the delimiter is the result of quote removal
       on word, and the lines in the here-document are not expanded.  If  word
       is  unquoted, all lines of the here-document are subjected to parameter
       expansion, command substitution, and arithmetic expansion, the  charac‐
       ter  sequence  \<newline>  is  ignored, and \ must be used to quote the
       characters \, $, and `.


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
