#### Docker command line

###### Dockerfile [Dockerfile](https://github.com/WeRockStar/Docker-Command-line/blob/master/Dockerfile.md)
```shell
    docker help <COMMAND> # push, run, start etc.

 # Docker Machine
    docker-machine create --driver=virtualbox <MACHINE_NAME> # Create driver 
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
    
# Docker Images More 
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
    docker run --expose=7000-8000 <CONTAINER_ID or CONTAINER_NAME>   #  Range of ports
    docker run -p 7000-8000:7000-8000 <CONTAINER_ID or CONTAINER_NAME>
    docker network ls # Docker networks
    docker port <CONTAINER_ID>    # See port 
    docker run --name nginx -d -p 8080:80 -p 8081:80 nginx # Two ports expose , but only one of them
    docker run --net=<NETWORK> <IMAGE_NAME> # Set network for image
    docker run -it --net=<NETWORK> --name=<CONTAINER_NAME> -d <IMAGE_NAME> # Set network for image
    docker run --net=none <IMAGE_NAME> # Running image without the network
    docker network inspect <NETWORK_NAME> # Inspect network information
    docker inspect <CONTAINER_ID> | grep IPAddress # Filter network information 
    docker network create <NETWORK_NAME> # Create simple network
    docker network disconnect <Network> <CONTAINER_ID or CONTAINER_NAME>  # Disconnect network

    - Linking containers (Can link only to the running container.)
    docker run -it --name=ubuntu --link mysql:mysql ubuntu # Link with mysql container
    more /etc/hosts  # Linking is persistent
    env | grep MYSQL  # Filter MYSQL environment variable

 # Docker Swarm
    docker swarm init   # Enable swarm mode
    docker node ls      # List of nodes

    # Multi Networking
    docker $(docker-machine config host01) run -d -p "8500:8500" -h "consul" progrium/consul -server -bootstrap
    docker-machine create -d virtualbox  --engine-opt="cluster-store=consul://$(docker-machine ip host01):8500" --engine-opt="cluster-advertise=eth1:0" host02
    docker-machine create -d virtualbox  --engine-opt="cluster-store=consul://$(docker-machine ip host01):8500" --engine-opt="cluster-advertise=eth1:0" host03

    - Host 02
    docker $(docker-machine config host02) network create -d overlay overlayNetwork
    docker $(docker-machine config host02) network ls
    # Run nginx web server in host02
    docker $(docker-machine config host02) run -itd --name=nginx --net=overlayNetwork nginx
    
    - Host 03 
    docker $(docker-machine config host03) network ls
    # Testing multi-host network, fetch index page from host03
    docker $(docker-machine config host03) run -it --net=overlayNetwork busybox

 # Docker Volume
    docker run -it -v /Users/<YOUR_USER>/<PATH>/:<CONTAINER_PATH> <IMAGE_NAME>  # Run ubuntu and create volume for our data
    docker volume ls  # List volume 
    docker volume ls -f dangling=true  # Filter volume
    docker volume ls -f driver=default # Filter volume with driver
    docker volume ls -f name=local   # Filter volume with volume name
    docker volume rm $(docker volume ls -qf dangling=true)  # Filter remove volume not a referencing any containers
    docker volume create --name <VOLUME_NAME>  # Create volume
    docker run -it -v <VOLUME_NAME>:/data ubuntu  # Run with volume and <VOLUME_NAME> volume will then be available for your container in /data.
    docker volume inspect <VOLUME_ID>  # Inspect information on volume
    docker volume rm <VOLUME_ID or VOLUME_NAME>  # Remove volume
    docker rm -v <CONTAINER_ID or CONTAINER_NAME>     # Remove a volume by referencing a container
    docker run --name docker-nginx -p 80:80 -d --volumes-from <CONTAINER_ID or CONTAINER_NAME> nginx  # Run nginx with volume referencing <CONTAINER_NAME> Container's

 # Working Docker-Hub   
    docker login --username=<Docker ID> --password=<PASSWORD>  # Login docker hub
    docker login --username<Docker ID> --password<PASSWORD> localhost:8080  # Login docker provide a registry's hostname
    docker logout
    docker search <IMAGE_NAME>  # Search images on docker hub
    more .docker/config.json  # Get the credentials from the local storage
    Remove login credentials for https://index.docker.io/v1/ 
```

