


1. make -C $(buildrootdir) BR2_EXTERNAL=$(externaldir) menuconfig

   **Notes:** before doing this, please finish the steps as below. 

2. if `${externaldir}` name is `"external"`, then create the files listed as below. 

   - Config.in  
   - external.desc  
   - external.mk    

3. Add the contents as below for these example files. 

   - external.desc
   
   ```
   name: developing
   desc: developing_config
   ```
   
   - external.mk
   
   ```
   include $(sort $(wildcard $(BR2_EXTERNAL_developing_PATH)/package/*/*.mk))
   ```
   
   - Config.in  
   
   ```
   source "$BR2_EXTERNAL_developing_PATH/package/Config.in"
   ```

