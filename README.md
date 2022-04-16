# Docker commands:
- `docker version`
- `docker ps`
- `docker rm`
- `docker rm $(docker ps -a -q)`
- `docker rmi <image-id>`
- `docker rmi $(docker images -a -q)`
- `docker pull <image-name>`
- `docker create -ti <image-name> --name <container-name>`
- `docker run -it --name <container-name> -d eon01/infinite`
- `docker network ls [OPTIONS]`
- `docker network rm <network-name>`
- `docker search <image-name>`
- `docker network create --driver nat <network-name>`
- `docker logs service 2>&1 | grep -C 5 "FATAL"`
- `docker container run <image name>`
- `docker container run -p 80:80 microsoft/iis:latest`
- `docker attach <container name>`
- `docker search <image name>`
- `docker pull <image name>`
- `docker images`
- `docker container start <container name>`
- `docker ps -a`
- `docker container attach <container name>`
- `docker container exec <container name> ls`
- `docker container stop <container name>`
- `docker container rm <container name>`
- `docker container rename <container name> <new container name>`
- `docker commit -m "Added web-server Apache2" -a "Evgeniy Tokmakov" 37def446ae84 tokmakov/apache2_ubuntu`
- `docker run -v /path/to/outer-dir:/path/to/inner-dir image-name`
- `docker inspect <container name>`
- `docker exec -it nginx /bin/bash`
- `docker run --name redis -v /root/docker-practice/1/redis/:/data/ -d redis`
------------------------------------------------
**Docker file:**

```
FROM php:7.2-cli
COPY script.php /script.php
RUN chmod +x /script.php
CMD php /script.php
```

```
docker build . --tag php-cli-script
```

```
FROM ubuntu:18.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

```
FROM ubuntu:18.04
LABEL maintainer="somebody@somewhere.com"
ENV ADMIN="somebody"
RUN ["exec-file", "first", "second"]
COPY . ./bin

WORKDIR /app
COPY . .
ENTRYPOINT ["php", "./app/script.php", "data"]
```

- `FROM` — использовать образ с предустановленным php:7.2-cli (имя:тег)
- `COPY` — копировать файл script.php из основной системы внутрь контейнера
- `RUN` — выполнить shell-команду в терминале контейнера (сделать скрипт исполняемым)
- `CMD` — выполнять эту shell-команду каждый раз при запуске контейнера

- `FROM` — задаёт базовый (родительский) образ
- `LABEL` — описывает метаданные (например, кто создал образ)
- `ENV` — устанавливает постоянные переменные среды
- `RUN` — выполняет команду и создаёт слой образа
- `COPY` — копирует в контейнер файлы и директории
- `ADD` — копирует файлы и папки в контейнер, может распаковывать .tar-файлы
- `CMD` — описывает команду с аргументами, которая выполняется при запуске контейнера
- `WORKDIR` — задаёт рабочую директорию для следующей инструкции
- `ARG` — задаёт переменные для передачи Docker во время сборки образа
- `ENTRYPOINT` — задает команду с аргументами для вызова во время выполнения контейнера
- `EXPOSE` — указывает на необходимость открыть порт
- `VOLUME` — создаёт точку монтирования для работы с постоянным хранилищем
------------------------------------------------
**Определения:**
- `Docker` — это система управления процессами приложения в контейнерах. Все процессы выполняются в изолированном пространстве, но в то же время на одном ядре, что позволяет экономить ресурсы основной системы. Docker не реализует собственную систему контейнеров, он использует LXC и выступает в качестве оболочки.
- `Docker volume` — это просто папка хоста, примонтированная к файловой системе контейнера. Так как технически она больше не принадлежит контейнеру, то последний можно смело удалять, пересоздавать заново, снова прикручивать к нему хостовые папки, и ничего с данными внутри не случится.
- `Docker Volumes (Том)` — это файловая система, которая расположена на хост-машине за пределами контейнеров. Тома представляют собой средства для постоянного хранения информации и могут совместно использоваться разными контейнерами. Созданием и управлением томами занимается Docker.
- `Dockerfile` — конфигурационный файл, описывающий пошаговое создание среды для работы приложения. В этом файле подробно описывается какие образы задействованы, какие команды будут выполнены и какие настройки будут применены. А движок Docker-а при запуске уже прочитает этот файл и создаст соответствующий образ.
- 
------------------------------------------------
- Комбинация опций `-i` и `-t` обеспечивает интерактивный доступ к командному процессору контейнера:
------------------------------------------------
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
------------------------------------------------
- https://tokmakov.msk.ru/blog/tags/303
- https://habr.com/ru/company/ruvds/blog/439980/
------------------------------------------------
# Вопросы:
  
1. Tag
2. Слои. Кэширование слоев
3. run —detach
4. Возможно ли прописать volumes в Docker-файле
5. Где хранятся логи контейнера. Как работает docker logs
6. ADD vs COPY
7. Как ограничить ресурсы контейнеру? (cpu/memory)
