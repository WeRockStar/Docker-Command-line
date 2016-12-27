#### Dockerfile instructions
```shell
    FROM <IMAGE_NAME>  # Base image, can have multiple FROM instructions in your image
    FROM <IMAGE_NAME>:<TAG>

    MAINTAINER <AUTHOR>  # Set author of generage image
    
    ADD <SOURCE_PATH or URL> <DESTINATION_PATH> . # Copy files from host into docker file system 
    ADD ["<SOURCE_PATH or URL>" "<DESTINATION_PATH>"]  # With source or destination path contain spaces  
```