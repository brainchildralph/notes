

Example
------

```
[
    {
        "id": "50389bde.add2b4",
        "type": "ui_chart",
        "z": "90015208.b2591",
        "name": "",
        "group": "f12b305.dd441d",
        "order": 12,
        "width": 0,
        "height": 0,
        "label": "{{msg.label}}",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "outputs": 1,
        "x": 550,
        "y": 60,
        "wires": [
            []
        ]
    },
    {
        "id": "6f3bc9dc.b25078",
        "type": "change",
        "z": "90015208.b2591",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "label",
                "pt": "msg",
                "to": "label test",
                "tot": "str"
            },
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "[{\"series\":[\"t\"],\"data\":[[{\"x\":\"5/1/2019, 15:44:45\",\"y\":28.87},{\"x\":\"5/1/2019, 15:45:23\",\"y\":28.97},{\"x\":\"5/1/2019, 15:46:02\",\"y\":29},{\"x\":\"5/1/2019, 15:46:41\",\"y\":29.15},{\"x\":\"5/1/2019, 15:47:20\",\"y\":29.14},{\"x\":\"5/1/2019, 15:47:58\",\"y\":29.28},{\"x\":\"5/1/2019, 15:48:37\",\"y\":29.22},{\"x\":\"5/1/2019, 15:49:16\",\"y\":29.32},{\"x\":\"5/1/2019, 15:49:55\",\"y\":29.29},{\"x\":\"5/1/2019, 15:50:33\",\"y\":29.46},{\"x\":\"5/1/2019, 15:51:12\",\"y\":29.67},{\"x\":\"5/1/2019, 15:51:51\",\"y\":29.81},{\"x\":\"5/1/2019, 15:52:29\",\"y\":29.96},{\"x\":\"5/1/2019, 15:53:08\",\"y\":29.97},{\"x\":\"5/1/2019, 15:53:47\",\"y\":29.96},{\"x\":\"5/1/2019, 15:54:25\",\"y\":29.96},{\"x\":\"5/1/2019, 15:55:04\",\"y\":29.84},{\"x\":\"5/1/2019, 15:55:43\",\"y\":29.79},{\"x\":\"5/1/2019, 15:56:22\",\"y\":29.81},{\"x\":\"5/1/2019, 15:57:00\",\"y\":29.82}]],\"labels\":[\"\"]}]",
                "tot": "json"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 60,
        "wires": [
            [
                "50389bde.add2b4"
            ]
        ]
    },
    {
        "id": "4c0054d5.65b8dc",
        "type": "inject",
        "z": "90015208.b2591",
        "name": "",
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 140,
        "y": 60,
        "wires": [
            [
                "6f3bc9dc.b25078"
            ]
        ]
    },
    {
        "id": "f12b305.dd441d",
        "type": "ui_group",
        "z": "",
        "name": "Collector",
        "tab": "1edde833.f1fbb8",
        "order": 1,
        "disp": true,
        "width": "6",
        "collapse": false
    },
    {
        "id": "1edde833.f1fbb8",
        "type": "ui_tab",
        "z": "",
        "name": "Test",
        "icon": "dashboard",
        "order": 1,
        "disabled": false,
        "hidden": false
    }
]


```
