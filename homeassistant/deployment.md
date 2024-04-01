# Deployment

### Setup
```
mkdir homeassistant
mkdir homeassistant/config
```
### Deploy Containers
```
docker-compose up 
```
### Update Containers
The following commands will update the containers
```
docker-compose build
docker-compose down
docker-compose up -d --force-recreate
docker rmi $(docker images -f "dangling=true" -q) -f
```