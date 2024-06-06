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

To pass user supplied values to container
```bash
docker run --name mysql -e MYSQL_ROOT_PASSWORD=1234 -d mysql
```

> [!NOTE]
> Whenever we need to pass user supplied values to container, we need to supply those values as environment variable using `-e` or `--env` flag

To view docker container resource consumption. 
> docker stats <container_name>

>docker stats <container_id>
```bash
docker stats 6e84
```
![image](https://github.com/tejasp77/DevOps/assets/165159032/9fe461d4-fd35-432d-99c9-741c00722e35)
It shows stats regarding consumption of cpu, ram, pids, traffic resources on which container running on host machine.
![image](https://github.com/tejasp77/DevOps/assets/165159032/a9adeaaf-580d-4af7-ae54-4ad7aec80f45)
For pid, we can run docker top <container_id> command to check how many process are running inside the container.

To get detailed information about container.
> docker inspect <container_name>

>docker inspect <container_id>
```bash
docker inspect 6e84
```




