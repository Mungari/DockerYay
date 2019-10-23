Useful docker commands:

------------------------------------------------------------------------------------------
docker save [-o FILENAME] IMAGE_NAME[:TAG]                                               
-o -> Output file (e.g file.tar) *can be gzipped, will be unzipped by load*              
                                                                                         
## docker save -o mysql.tar registry.access.redhat.com/rhscl/mysql-56-rhel7 ## EXAMPLE   
------------------------------------------------------------------------------------------


------------------------------------------------------------------------------------------
docker load [-i FILENAME]                                                                
                                                                                         
-i -> input                                                                              
## docker load -i mysql.tar ##                                                           
------------------------------------------------------------------------------------------


------------------------------------------------------------------------------------------
docker tag IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]                              
                                                                                         
-i -> input                                                                              
## docker tag nginx nginx ## -> docker push nginx                                        
------------------------------------------------------------------------------------------

