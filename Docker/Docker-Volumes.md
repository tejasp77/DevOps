**Container Persistent Data Problem**
- Containers are immutable : Once deploy never change, only re-deploy.
- Config Change or version Upgrade need re-deploy.
- By default all files created inside a container are stored on a writable container layer.
- The data doesn’t persist when that container no longer exists, and it can be difficult to get the data out of the container if another process needs it

Docker has two options for containers to store files in the host machine, so that the files are persisted even after the container stops.
- Volumes
- Bind Mount

**Volumes** 
- Volumes are stored in a part of the host filesystem which is managed by Docker. 
- Volumes are created and Managed by Containers.
- Volumes can be create by Volume Command in Docker File.
- When you create a volume, it is stored within a directory on the Docker host machine.
- Volumes can not be removed when user destroy the containers.

Run MySQL
```bash
docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True mysql
```

List volumes 
```bash
docker volumes ls
```

Inspect Volumes
```bash
docker volume inspect
```

**Named volumes**

Run MySQL with named Volume
```bash
docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True --mount source=mysql-db, target=/var/lib/mysql mysql
```
```bash
docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/ mysql mysql
```

Create Volumes 
```bash
docker volume create <NAME>
```

Remove Volume 
```bash
docker volume rm <NAME>
```
