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





