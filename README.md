#### Docker command line
```shell
    
    docker-machine create --driver=virtualbox default
    eval "$(docker-machine env default)"

    docker help <HELP_SOMETHING>
    
    docker ps 
    docker ps -a

    docker-machine ls
    docker-machine start default
    docker-machine ssh default
    docker-machine stop <MACHINE_NAME>
    docker-machine ip

    docker logs <CONTAINER_ID>
    docker inspect <CONTAINER_ID>

    docker run —name <CONTAINER_NAME> -v <LOCAL_PATH>:<CONTAINER_PATH>:ro -p <LINUX_POST>:<CONTAINER_PORT> -d <IMAGE_NAME>
    docker stop <CONTAINER_ID>
    docker run/start <CONTAINER_ID>
    docker rm <CONTAINER_ID>
    docker rm <CONTAINER_ID> `docker ps -aq` or docker rmi $(docker images -q)
    docker rmi $(docker images -q -f dangling=true) # Remove all un-tagged

    docker exec -it <CONTAINER_ID> bash
```

