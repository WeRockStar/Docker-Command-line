#### Docker command line
```shell
    docker help <COMMAND> # push, run, start etc.

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
    docker rm -v $(docker ps -q -f status=exited) # Remove with filter status of container
    docker rm <CONTAINER_ID> `docker ps -aq` # Remove all container
    docker stats <CONTAINER_ID> # Live stream container stats 
    docker upadate <CONTAINER_ID> # Update configuration container
    docker stop <CONTAINER_ID> # Stop container
    # start / stop / restart / pause / unpause
    docker run/start <CONTAINER_ID> # Start with new container and run container

    docker logs <CONTAINER_ID> # Log of container 
    docker inspect <CONTAINER_ID> # Inspect low-level information on container
    docker exec -it <CONTAINER_ID> bash # Interactive option with container 
    
# Docker Images
    docker images # Show list image
    docker images -a # Show list image
    docker rmi $(docker images -q) # Remove all image
    docker rmi $(docker images -q -f dangling=true) # Remove all un-tagged
    docker history <IMAGE_NAME> # Show history of docker image 
    docker commit <CONTAINER_ID> <IMAGE_NAME> # Save changes you have made to the container
    docker run -it ubuntu /bin/bash # Run image with Interactive option
    docker run <IMAGE_NAME> mkdir /home/test # Create a new folder
    docker run —name <CONTAINER_NAME> -v <LOCAL_PATH>:<CONTAINER_PATH>:ro -p <LINUX_POST>:<CONTAINER_PORT> -d <IMAGE_NAME> # Run container with define container name, volume path and specific image

 # Docker Registry
    docker login    # Login into Docker regsitry
    docker logout   # Logout Docker regsitry
    docker pull     # Pull image or repository from a Registry or Docker hub
    docker push     # Psuh image or repository into a Registry or Docker hub
    docker search   # Search Docker hub for images

 # Docker Network
    docker network ls # Docker networks
    docker run --net=<NETWORK> <IMAGE_NAME> # Set network for image
    docker run -it --net=<NETWORK> --name=<CONTAINER_NAME> -d <IMAGE_NAME> # Set network for image
    docker run --net=none <IMAGE_NAME> # Running image without the network
    docker network inspect <NETWORK_NAME> # Inspect network information
    docker inspect <CONTAINER_ID> | grep IPAddress # Filter network information 
    docker network create <NETWORK_NAME> # Create simple network
    docker network disconnect <Network> <CONTAINER_ID or CONTAINER_NAME>  # Disconnect network
```

