
SDK
======

> TI-15-4-STACK-GATEWAY-LINUX-SDK_2.09.00.09


Code Trace
==========    

> 
> cscope    
> =======
> 
> ```
> find `pwd` -name "*.[ch]" > cscope.files
> cscope -bkq -i cscope.files
> ```
>  
> ctags
> =======
>
> ```
> ctags -L cscope.files
> ```
> 
> 
> 
> Console Initialization
> =====
> 
>> Collector_init    
>>> Csf_init    
>>>> initConsoleCmd    
>>>>> 
> 
> 
> example/collector/linux_main.c: 
> ======
> 
> Entry main()
> 
>> Parsing config with `cfg_callback`    
>> APP_main()
>> 
> 
> 
> example/collector/appsrv.c:  
> ======
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


Test
======

> Netcat (nc)
> =====
> 
> ```
> ip=192.168.2.165
> echo -ne "\x00\x00\x4a\x0b" | nc -q -1 ${ip} 5000     # wait forever
> ```



