#### Docker command line
```shell
    docker-machine create --driver=virtualbox default # Create driver 
    eval "$(docker-machine env default)"

    docker help <HELP_SOMETHING>
    
    docker ps # Show list running container 
    docker ps -a # Show all list container

    docker-machine ls # Show list of machine
    docker-machine start default # Start docker machine
    docker-machine ssh default # Work shell on the docker machine
    docker-machine stop <MACHINE_NAME> # Stop docker machine
    docker-machine ip # Show ip docker machine
 
    docker logs <CONTAINER_ID> # Log of container 
    docker inspect <CONTAINER_ID> # Inspect on container
    docker history <IMAGE_NAME> # Show history of docker image 

    docker run —name <CONTAINER_NAME> -v <LOCAL_PATH>:<CONTAINER_PATH>:ro -p <LINUX_POST>:<CONTAINER_PORT> -d <IMAGE_NAME> # Run container with define container name, volume path and specific image
    docker stop <CONTAINER_ID> # Stop container
    docker run/start <CONTAINER_ID> # Start with new container and run container
    docker rm <CONTAINER_ID>  # Remove container with container id
    docker rm <CONTAINER_ID> `docker ps -aq` or docker rmi $(docker images -q) # Remove all container
    docker rmi $(docker images -q -f dangling=true) # Remove all un-tagged

    docker exec -it <CONTAINER_ID> bash # Interactive with container 
```

