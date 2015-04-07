# Docker commands
`docker ps` List sevices

`docker images` List images

`docker rmi -f $(docker images -qf "dangling=true")` Remove unused images

`docker system prune` Remove unused data

`docker rm $(docker ps -a -q)` Remove all containers

`docker rmi $(docker images -q)` Remove all images

`docker volume rm $(docker volume ls -q -f dangling=true)` Remove all  unused volumes

`docker exec -it container_name /bin/bash` Run a command in a running container

```docker run 
	-p "4567:4567"
	--entrypoint bash 
	--rm 
	-it 
	--volumes-from volume_id
	image_id
```
Run a command in a new container of `image_id`:

*  Mapping the port 4567 to 4567
*  Overriding the entrypoint to `bash`
*  Automatically removing the container on exit
*  With and allocated TTY connected to the container’s stdin
*  	Mounting volumes from the specified container(s)

### Docker exec vs docker run  
When using `docker run` a temporary docker container is created  and stopped(not terminated) after the command has finished running. `Docker exec` needs a running container to take the command.

### Networking
`docker inspect docker_api-interface_1` To show network information

```
docker run -p "4567:4567" --rm --net-alias webui.local fd92207d57fd
docker run -it --rm --net docker_default --entrypoint bash 37a9c9e04c28
```
Would start the first container with the network alias `webui.local` and would connect the second container to the docker default network. 
 

# Docker compose commands
`docker-compose up` to start the services. Build is a side effect that happens only once if anything needs to be build

`docker-compose up --build` Always build

`docker-compose down` Kill all containers

`docker-compose pull` Pull latest images

`docker-compose exec container_name bash` Execute container

## In a docker-compose file
`volumes: "/Users/joan_mr/docker-data/mysqlcore:/var/lib/mysql"` Will map the container data to the local machine
