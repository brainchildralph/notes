


1. make -C $(buildrootdir) BR2_EXTERNAL=$(externaldir) menuconfig

   **Notes:** before doing this, please finish the steps as below. 

2. if `${externaldir}` name is `"external"`, then create the files listed as below. 

   - Config.in  
   - external.desc  
   - external.mk

