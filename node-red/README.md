
#### Node-red Simple Readme

---

##### Use the settings file

> ```
> node-red -s node-red-settings.js
> ```
> 
> **指定使用者資料夾**
> ```
> node-red -s node-red-settings.js -u $userDir
> ```

##### flows  file path:

> ```
> ...
> flowFile: 'flows.json',
> ...
> ```

##### Access the UI

> http://localhost:1880


##### Listen IP settings

> ```
> ...
> uiHost: "0.0.0.0"
> ...
> ```

##### UI login

> Uncomment node-red-settings: 
> 
> ```
> adminAuth: {
>     type: "credentials",
>     users: [{
>         username: "admin",
>         password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.",
>         permissions: "*"
>     }]
> }
> ```
> 
> Create password: 
> 
> ```
> node-red-admin hash-pw
> ```
> 




