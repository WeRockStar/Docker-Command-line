#### Docker command line
```shell
    docker help <HELP_SOMETHING>


 # Docker Machine
    docker-machine create --driver=virtualbox default # Create driver 
    eval "$(docker-machine env default)"
    docker-machine ls # Show list of machine
    docker-machine start default # Start docker machine
    docker-machine ssh default # Work shell on the docker machine
    docker-machine stop <MACHINE_NAME> # Stop docker machine
    docker-machine ip # Show ip docker machine

# Docker Container
    docker ps # Show list running container 
    docker ps -a # Show all list container you have on youre system

    docker rm <CONTAINER_ID>  # Remove container with container id
    docker rm <CONTAINER_ID> `docker ps -aq` # Remove all container
    docker rm -v $(docker ps -q -f status=exited) # Remove with filter status of container
    docker stop <CONTAINER_ID> # Stop container
    docker run/start <CONTAINER_ID> # Start with new container and run container

    docker logs <CONTAINER_ID> # Log of container 
    docker inspect <CONTAINER_ID> # Inspect low-level information on container
    docker exec -it <CONTAINER_ID> bash # Interactive option with container 
    
# Docker Images
    docker images # Show list image
    docker rmi $(docker images -q) # Remove all image
    docker rmi $(docker images -q -f dangling=true) # Remove all un-tagged
    docker history <IMAGE_NAME> # Show history of docker image 
    docker run -it ubuntu /bin/bash
    docker run —name <CONTAINER_NAME> -v <LOCAL_PATH>:<CONTAINER_PATH>:ro -p <LINUX_POST>:<CONTAINER_PORT> -d <IMAGE_NAME> # Run container with define container name, volume path and specific image

```

