# Docker Compose


### Update All Containers
The following commands with the existing Docker-Compose file will update all of the containers.

```
docker-compose pull
docker-compose up --force-recreate --build -d
docker image prune -f
```
