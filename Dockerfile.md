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

    # LABEL description="This is description"
    LABEL "KEY"="VALUE"    # Add meta data to images

    # Sample,  ENV JAVA_HOME /var/lib/java8
    # ENV PATH /var/lib/tomcat8/bin:$PATH 
    ENV <NAME_ENV> <VALUE_ENV_PATH>  # Set environment path

    # Expose port allowing income network traffic to container
    EXPOSE <PORT>

    #  Executing instruction for Dockerfiles (Build time)
    #  CMD instruction is executed when the container is launched by executing `docker run` on the newly created image
    #  CMD (Runtime)
    #  RUN used to build the image, by creating a new layer on top of the previous one which is committed.
    RUN <COMMAND> 


    # User use when running images
    # Affects the user for any RUN, CMD, and ENTRYPOINT
    USER <USER>
    
    # Example
    USER docker
    RUN groundadd docker && useradd docker -r -g docker docker

    # Great way of storing and retrieving data from the Docker container.
    # Mount a directory inside your container and store files created or edited inside that directory on your host's disk out side the container file structure
    # -v will mount the existing files from your operating system inside your Docker container and VOLUME  will create a new, empty volume on your host and mount it inside your container
    VOLUME PATH 
    VOLUME ["PATH"]


    # Add working directory for any instruction, CMD, RUN, ENTRYPOINT, ADD 
    WORKDIR PATH
    
    # Passing argument at build time (--build-arg <VARIABLE_NAME>=<VALUE>) 
    ARG ARGUMENT


    # Test a container to check that it is still working, passes = healthy, failure = unhealthy
    # Value can be 0,1. 0 = healthy, 1 = wrong and container not working correctly.
    HEALTHCHECK --interval=<interval> --timeout=<timeout>  CMD <command>

    # Default shell used for the shell form of commands. It can be zsh, csh, or tcsh
    SHELL ["EXRCUTABLE", "PARAMETER"]
    
```