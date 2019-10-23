Useful docker commands:

------------------------------------------------------------------------------------------
docker save [-o FILENAME] IMAGE_NAME[:TAG]                                               
-o -> Output file (e.g file.tar) *can be gzipped, will be unzipped by load*
saves a dockerImage
                                                                                         
## docker save -o mysql.tar registry.access.redhat.com/rhscl/mysql-56-rhel7  
------------------------------------------------------------------------------------------


------------------------------------------------------------------------------------------
docker load [-i FILENAME]                                                                
loads a dockerImage                                                                                         
-i -> input                                                                              
## docker load -i mysql.tar                                                            
------------------------------------------------------------------------------------------


------------------------------------------------------------------------------------------
docker tag IMAGE[:TAG] [REGISTRYHOST/][USERNAME/]NAME[:TAG]                              
 tags an image                                                                                        
-i -> input                                                                              
## docker tag nginx nginx -> docker push nginx           
remove tags:
## docker rmi [REGISTRYHOST/][USERNAME/]NAME[:TAG]
------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------
docker rmi [OPTIONS] IMAGE [IMAGE...] (ref by name OR ID)

containers must be stopped before removing an image
## docker rmi $(docker images -q) -> removes all images NOT used by any container.
------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
--author=""
--message=""

commits a container to a repo, as is.

## docker commit mysql-basic mysql-custom
------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------
## DOCKERFILE SECTION BEGINS HERE
------------------------------------------------------------------------------------------

------------------------------------------------------------------------------------------
Steps:
1) Create working dir
2) Write Dockerfile spec
3) Build

Commands/syntax:
1) mkdir
2) #COMMENT
   *INSTRUCTION* arguments
   example:
# This is a comment line
FROM rhel7.3 
LABEL description="This is a custom httpd container image" 
MAINTAINER John Doe <jdoe@xyz.com> 
RUN yum install -y httpd 
EXPOSE 80 
ENV LogLevel "info" 
ADD http://someserver.com/filename.pdf /var/www/html -> \
                                                          -=> both use root as the owner of the file. Use a RUN instruction to change perms after. 
COPY ./src/ /var/www/html/ ---------------------------> /
USER apache 
ENTRYPOINT ["/usr/sbin/httpd"]  
CMD ["-D", "FOREGROUND"] 

3) docker build -t NAME:TAG DIR (if working directory is current directory "." can be used)
------------------------------------------------------------------------------------------
