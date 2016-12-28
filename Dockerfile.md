#### Dockerfile instructions
```shell
    FROM <IMAGE_NAME>  # Base image, can have multiple FROM instructions in your image
    FROM <IMAGE_NAME>:<TAG>

    MAINTAINER <AUTHOR>  # Set author of generage image
    
    ADD <SOURCE_PATH or URL> <DESTINATION_PATH>  # Copy files from host into docker file system 
    ADD ["<SOURCE_PATH or URL>" "<DESTINATION_PATH>"]  # With source or destination path contain spaces  

    COPY <SOURCE_PATH or URL> <DESTINATION_PATH>  # Copy files from host into docker file system 
    COPY ["<SOURCE_PATH or URL>" "<DESTINATION_PATH>"]  # With source or destination path contain spaces  
    # COPY supports only the basic copying of local files into the container. ADD features some more, such as archive extraction, downloading files through URL

    CMD ["EXRCUTABLE", "PARAMETER" , "PARAMETER"]  # Provide default for executable container
    # This will not invoke a command shell.
    # ENTRYPOINT ["COMMAND", "PARAMETER", "PARAMETER"]
    ENTRYPOINT  ["EXRCUTABLE", "PARAMETER" , "PARAMETER"]  # ENTRYPOINT was developed for more customization, and some functionality overlaps between those two instructions
    # If you want using shell
    # ENTRYPOINT [ "sh", "-c", "echo $HOSTNAME" ]
    ENTRYPOINT ["sh", "-c", "echo $HOSTNAME" ]  # Using shell processing

    LABEL "KEY"="VALUE"    # Add meta data to images
    
```