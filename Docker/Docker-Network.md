### Docker Network
- Connect Containers to Other Containers and Connect Containers to Host machine.
- Docker containers and services can be connected with each other.
- Containers and Services don’t need to be aware, where they are deployed.
- Container and Services can communicate, Whether your Docker hosts run Linux, Windows, or a mix of OS.
- Each Container connect to virtual private network called bridge is default Network driver of Docker.
- Containers which are deployed in default bridge network will able to communicate with each other by using the IP addresses.
- Bridge network is an isolated with in the cluster the containers in different clusters can’t communicate with the container in the different cluster.
- Best Practice to create Networks:
  - network “sql_php_nwt” for mySQL and PHP Containers
  - network “mongo_nwt” for mongo and PHP Container

Start Container to allow traffic from Port on Host Machine
```bash
docker container run -p <host_port>:<docker_port> -d image
```

Find the traffic and protocol on container
```bash
docker port <container_id>
```

Find Docker Container IP
```bash
docker inspect <container_id>
```

Show All networks
```bash
docker network ls
```

Filter the Networks. To Filter all bridge network
```bash
docker network -f drive=bridge
```

To find all Network IDs and Drivers
```bash
docker network ls --format "{{.ID}}: {{.Driver}
```
