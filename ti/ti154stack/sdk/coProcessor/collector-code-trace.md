
SDK
------

> TI-15-4-STACK-GATEWAY-LINUX-SDK_2.09.00.09


Code Trace
-----   

> 
> cscope    
> -----
> 
> ```
> find `pwd` -name "*.[ch]" > cscope.files
> cscope -bkq -i cscope.files
> ```
>  
> ctags
> -----
>
> ```
> ctags -L cscope.files
> ```
> 
> 
> 
> Console Initialization
> -----
> 
>> Collector_init    
>>> Csf_init    
>>>> initConsoleCmd    
>>>>> 
> 
> 
> example/collector/linux_main.c: 
> -----
> 
> Entry main()
> 
>> Parsing config with `cfg_callback`    
>> APP_main()
>> 
> 
> 
> example/collector/appsrv.c:  
> ------
> 
> APP_main()
> 
>>  create 2 threads
>>  - server-thread:     
       appsrv_server_thread()
>>  - collector-thread:   
       collector_thread()
>> 
> 

Trace appsrv_server_thread()    
> appsrv_server_thread()    
>> pCONN->socket_interface = appClient_mt_interface_template    
>> s2appsrv_thread()    
>>> MT_MSG_interfaceCreate(recv data)()
>>>> mt_msg_rx_thread()    
>>>>> mt_msg_rx()    
>>>>>> mt_msg_rx_bytes()    
>>>>>
>>>>
>>> appsrv_handle_appClient_request()   
>>>> APPSRV_GET_NWK_INFO_REQ    
>>>> appsrv_processSetJoinPermitReq()    
>>>>> Cllc_setJoinPermit()    
>>>>>> **// Send update state changed message**    
>>>>>> updateState()     
>>>>> **// Send status message**      
>>>>> send_AppSrvJoinPermitCnf()     
>>>>
>>>
>> 
> 
> appsrv_processTxDataReq    
> -----
> 
> Send TX Data    
>> Smsgs_cmdIds_toggleLedReq     
>> 
>

Test
-----

> Netcat (nc)
> -----
> 
> Example:   
> -----
> 
>> ```
>> ip=192.168.2.165
>> echo -ne "\x00\x00\x4a\x0b" | nc -q -1 ${ip} 5000     # wait forever
>> ```
>>
>> Permit Join ON/OFF
>> -----
>>
>>> ```
>>> echo -ne "\x04\x00\x4a\x0b\xff\xff\xff\xff" | nc -q -1 ${ip} 5000     # Permit Join On
>>> echo -ne "\x04\x00\x4a\x0b\x00\x00\x00\x00" | nc -q -1 ${ip} 5000     # Permit Join Off
>>> ```
>>>
>>
>> Toggle Sensor LED
>> -----
>>
>>> ```
>>> echo -ne "\x03\x00\x4a\x0d\x06\x01\x00" | nc -q -1 ${ip} 5000     #  Toggle Device 0x0001 LED
>>> ```
>>
>> Config Sensor
>> -----
>>
>>> ```
>>> echo -ne "\x09\x00\x4a\x0d\x01\x01\x00\x00\x00\x10\x27\x19\x00" | nc -q -1 ${ip} 5000
>>> ```
>> 
