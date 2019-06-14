
#### Node-red Simple Readme

---

##### Use the settings file

> ```
> node-red -s node-red-settings.js
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
>         password: "abash8.",
>         permissions: "*"
>     }]
> }
> ```

> Create password: 
> 
> ```
> node-red-admin hash-pw
> ```

