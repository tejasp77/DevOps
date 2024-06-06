To verify version of docker install on machine
```bash
docker version`
```

To verify docker engine and details
```bash
docker info
```

List all docker commands
```bash
docker
```

To search for docker images from docker hub
> docker search <image_name>
```bash
docker search nginx
```

To start nginx web server in docker
> docker container run --publish <host_port>:<container_port> <image_name>
```bash
docker container run --publish 8080:80 nginx
```
> [!NOTE]
> This will run the container in foreground process. To stop container foreground process, press `ctrl+c`

To start container in background or detach mode
> docker container run --publish <host_port>:<container_port> --detach <image_name>
```bash
docker container run --publish 8080:80 --detach nginx
```

To list running containers
```bash
docker container ls
```

To list all running and stopped containers
```bash
docker container ls -a
```

To stop docker container
> docker container stop <container_id>

> docker container stop <container_name>
```bash
docker container stop 89c5
```

To start existing container
> docker container start <container_id>

> docker container start <container_name>
```bash
docker container start 23d9
```
> [!IMPORTANT]
> **run:** start a new container always and **start:** start a existing container

To define container name
> docker container run --publish <host_port>:<container_port> --detach --name <container_name> <image_name>
```bash
docker container run --publish 8080:80 --detach --name mynginx nginx
```

To see logs of a specific container
> docker container logs <container_id>

> docker container logs <container_name>
```bash
docker container logs 87c34
```

To see process running inside the container
> docker container top <container_id>
```bash
docker container top 11d9
```

To see specific process running in local machine. for example nginx
```bash
ps -ef | grep nginx
```

To remove all unused containers
> docker container rm <space_seperated_container_id>

> docker container rm <space_seperated_container_name>
```bash
docker container rm 33p4 881c 22a8
```




