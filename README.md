# Docker commands:
- `docker version`
- `docker ps`
- `docker rm`
- `docker rmi <image-id>`
- `docker pull <image-name>`
- `docker create -ti <image-name> --name <container-name>`
- `docker run -it --name <container-name> -d eon01/infinite`
- `docker network ls [OPTIONS]`
- `docker network rm <network-name>`
- `docker search <image-name>`
- `docker network create --driver nat <network-name>`
- `docker logs service 2>&1 | grep -C 5 "FATAL"`
- `docker container run <image name>`
- - `docker container run -p 80:80 microsoft/iis:lastest`

*Windows PowerShell:*
- `docker rm $(docker ps -aq)`

docker run -d -p 5000:5000 training/webapp
- Порты: ```<externalPort>:<internalContainerPort>``` 

# Docker help:
- No matching manifest for windows/amd64 in the manifest list entries:
> 1. Right click Docker icon in the Windows System Tray
> 2. Go to Settings
> 3. Daemon
> 4. Advanced
> 5. Set the "experimental": true
> 6. Restart Docker

- Create **docker network**:
Error response from daemon: could not find plugin bridge in v1 plugin registry: plugin not found

> docker network create --driver nat network-name

# Docker engine:
- https://habr.com/ru/company/ruvds/blog/439978/
----------------
# Вопросы:
  
1. Tag
2. Слои. Кэширование слоев
3. run —detach
4. Возможно ли прописать volumes в Docker-файле
5. Где хранятся логи контейнера. Как работает docker logs
