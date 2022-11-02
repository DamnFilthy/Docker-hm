# Docker-hm

# Задание 1 - Docker CLI

### Загрузите образ busybox последней версии
- docker search busybox 

``` 
NAME                                DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
busybox                             Busybox base image.                             2795      [OK]
radial/busyboxplus                  Full-chain, Internet enabled, busybox made f…   49                   [OK]
yauritux/busybox-curl               Busybox with CURL                               18
arm32v7/busybox                     Busybox base image.                             10
arm64v8/busybox                     Busybox base image.                             4
odise/busybox-curl                                                                  4                    [OK]
i386/busybox                        Busybox base image.                             3
busybox42/zimbra-docker-centos      A Zimbra Docker image, based in ZCS 8.8.9 an…   2                    [OK]
s390x/busybox                       Busybox base image.                             2
prom/busybox                        Prometheus Busybox Docker base images           2                    [OK]
joeshaw/busybox-nonroot             Busybox container with non-root user nobody     2
p7ppc64/busybox                     Busybox base image for ppc64.                   2
vukomir/busybox                     busybox and curl                                1
spotify/busybox                     Spotify fork of https://hub.docker.com/_/bus…   1
busybox42/nginx_php-docker-centos   This is a nginx/php-fpm server running on Ce…   1                    [OK]
ppc64le/busybox                     Busybox base image.                             1
amd64/busybox                       Busybox base image.                             1
ibmcom/busybox-ppc64le                                                              0
busybox42/alpine-pod                                                                0
ibmcom/busybox-amd64                                                                0
antrea/busybox                                                                      0
openebs/busybox-client                                                              0
ibmcom/busybox                                                                      0
rancher/busybox                                                                     0
arm32v5/busybox                     Busybox base image.                             0
```

- docker pull busybox
```
Using default tag: latest
latest: Pulling from library/busybox
22b70bddd3ac: Pull complete
Digest: sha256:6bdd92bf5240be1b5f3bf71324f5e371fe59f0e153b27fa1f1620f78ba16963c
Status: Downloaded newer image for busybox:latest
docker.io/library/busybox:latest
```

### Запустите новый контейнер busybox с командой ping сайта netology.ru, и количеством пингов 7, поименуйте контейнер pinger
- docker run --name pinger busybox ping netology.ru -c 7
```
PING netology.ru (188.114.99.224): 56 data bytes

--- netology.ru ping statistics ---
7 packets transmitted, 0 packets received, 100% packet loss
```

### Выведите на список всех контейнеров - запущенных и остановленных
- docker container ls -a
```
CONTAINER ID   IMAGE                        COMMAND                  CREATED          STATUS                      PORTS                                            NAMES
7c670138e77b   busybox                      "ping netology.ru -c…"   38 seconds ago   Exited (1) 21 seconds ago                                                    pinger
```

### Выведите на экран логи контейнера с именем pinger
- docker logs pinger
```
PING netology.ru (188.114.99.224): 56 data bytes

--- netology.ru ping statistics ---
7 packets transmitted, 0 packets received, 100% packet loss
```

### Запустите второй раз контейнера с именем pinger 
- docker restart pinger
```
pinger
```

### Выведите на список всех контейнеров - запущенных и остановленных
- docker container ls -a
```
CONTAINER ID   IMAGE                        COMMAND                  CREATED              STATUS                     PORTS                                            NAMES
7c670138e77b   busybox                      "ping netology.ru -c…"   About a minute ago   Exited (1) 3 seconds ago                                                    pinger
```

### Выведите на экран логи контейнера с именем pinger
- docker logs pinger
```
PING netology.ru (188.114.99.224): 56 data bytes

--- netology.ru ping statistics ---
7 packets transmitted, 0 packets received, 100% packet loss
PING netology.ru (188.114.98.234): 56 data bytes

--- netology.ru ping statistics ---
7 packets transmitted, 0 packets received, 100% packet loss
```

### Определите по логам общее количество запусков команды ping и какое общее количество отправленых запросов
- 2 запуска, 14 запросов

### Удалите контейнер с именем pinger
- docker container rm pinger
```
pinger
```

### Удалите образ busybox
- docker image rm busybox
```
Untagged: busybox:latest
Untagged: busybox@sha256:6bdd92bf5240be1b5f3bf71324f5e371fe59f0e153b27fa1f1620f78ba16963c
Deleted: sha256:bc01a3326866eedd68525a4d2d91d2cf86f9893db054601d6be524d5c9d03981
Deleted: sha256:0438ade5aeea533b00cd75095bec75fbc2b307bace4c89bb39b75d428637bcd8
```
