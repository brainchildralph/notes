
Creat Buffer
------

Sample:
```
> new Buffer('010203', 'hex');
```

Result: 
```
<Buffer 01 02 03>
```

Sample: 
```
new Buffer('010203'); // different from previous one
```

Result: 
```
Buffer 30 31 30 32 30 33>
```

Sample: 
```
Buffer.from([0x01,0x02,0x03]);
```

Result: 
```
<Buffer 01 02 03>
```


slice
-----

- 不是創建新的 Buffer
- buffer 起始點為 0
- start 為切割的點，並包含。
- end 為結束的點，並不包含。

```
buffer.slice(start, end); 
```

