

Reference
------
- [Admin API Methods](https://nodered.org/docs/api/admin/methods/)

Example
------

```
[
    {
        "id": "43acdee.3c1312",
        "type": "inject",
        "z": "90015208.b2591",
        "name": "",
        "topic": "",
        "payload": "",
        "payloadType": "str",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 110,
        "y": 580,
        "wires": [
            [
                "e2643e2b.17fe8"
            ]
        ]
    },
    {
        "id": "8dc4a780.cd2268",
        "type": "http request",
        "z": "90015208.b2591",
        "name": "http: Localhost",
        "method": "POST",
        "ret": "txt",
        "paytoqs": false,
        "url": "http://localhost:1880/auth/token",
        "tls": "",
        "proxy": "",
        "authType": "basic",
        "x": 480,
        "y": 580,
        "wires": [
            [
                "39f0f1ae.6223fe"
            ]
        ]
    },
    {
        "id": "e2643e2b.17fe8",
        "type": "function",
        "z": "90015208.b2591",
        "name": "http data",
        "func": "msg.payload={\n    \"client_id\":\"node-red-admin\",\n    \"grant_type\":\"password\",\n    \"scope\":\"*\",\n    \"username\":\"*****\",\n    \"password\":\"********\"\n}\nmsg.headers={\n//  \"content-type\":\"application/x-www-form-urlencoded\"\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 280,
        "y": 580,
        "wires": [
            [
                "8dc4a780.cd2268"
            ]
        ]
    },
    {
        "id": "39f0f1ae.6223fe",
        "type": "json",
        "z": "90015208.b2591",
        "name": "",
        "property": "payload",
        "action": "",
        "pretty": false,
        "x": 650,
        "y": 580,
        "wires": [
            [
                "7eaf89b2.731c58",
                "7b5c0b5a.9492c4"
            ]
        ]
    },
    {
        "id": "7fa4b6c9.20fe88",
        "type": "http request",
        "z": "90015208.b2591",
        "name": "http: Localhost",
        "method": "POST",
        "ret": "txt",
        "paytoqs": false,
        "url": "http://localhost:1880/flows",
        "tls": "",
        "proxy": "",
        "authType": "basic",
        "x": 560,
        "y": 640,
        "wires": [
            []
        ]
    },
    {
        "id": "7b5c0b5a.9492c4",
        "type": "function",
        "z": "90015208.b2591",
        "name": "http data",
        "func": "access_token=msg.payload.access_token; \ntoken_type=msg.payload.token_type; \nauth=token_type+' '+access_token; \ndelete msg.payload; \nmsg.headers = {\n    \"Node-RED-Deployment-Type\":\"reload\",\n    \"Authorization\": auth\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 380,
        "y": 640,
        "wires": [
            [
                "7fa4b6c9.20fe88"
            ]
        ]
    }
]
```

