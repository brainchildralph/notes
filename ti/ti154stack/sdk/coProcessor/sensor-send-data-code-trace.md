


APPSRV_DEVICE_DATA_RX_IND
-----

- define 9 in appsrv.h
- appsrv_deviceRawDataUpdate() in appsrv.c
- Cmd1: 9
- Sensor sends data to collector and then appSrv update rx raw data


Example Packet
------

```
[84,0,74,9,2,1,0,242,5,234,116,161,28,0,75,18,0,25,0,24,0,24,0,1,0,0,0,46,0,46,0,64,0,64,0,64,0,1,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,70,83,0,0,0,0,0,0,26,0,34,0,144,95,1,0,112,23,0,0,0,0,0,0,0,0,0,0,0]
```

> Use node.js to parsing
> -----
> 
> ```
> # node
> > var rxData=Buffer.from([84,0,74,9,2,1,0,242,5,234,116,161,28,0,75,18,0,25,0,24,0,24,0,1,0,0,0,46,0,46,0,64,0,64,0,64,0,1,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,70,83,0,0,0,0,0,0,26,0,34,0,144,95,1,0,112,23,0,0,0,0,0,0,0,0,0,0,0]);
> > console.log(rxData.toString("hex"))
>   54004a09020100f205ea74a11c004b1200190018001800010000002e002e004000400040000100010001000000000000000000000000000000000046530000000000001a002200905f010070170000000000000000000000
> > var addrMode=rxData[4];
> > var shortAddr=new Buffer(rxData.slice(5,7)).swap16().toString('hex'); // if addrMode is 2
> > var rssi=rxData.readInt8(7); 
> > 
> > 
> ```
> 

processOadData()
------

- collector.c
- smsgs.h
  ```
      /*! OAD mesages, sent/received from both collector and sensor */
      Smsgs_cmdIds_oad = 9,
  ```
- Trace
  > processOadData()
  >> OADProtocol_ParseIncoming()
  >>> processOadImgBlockRsp()
