# Docker-hm

# Задание 1 - Docker CLI

### Загрузите образ busybox последней версии
- docker search busybox 
- docker pull busybox

### Запустите новый контейнер busybox с командой ping сайта netology.ru, и количеством пингов 7, поименуйте контейнер pinger
- docker run --name pinger busybox ping netology.ru -c 7

### Выведите на список всех контейнеров - запущенных и остановленных
- docker container ls -a

### Выведите на экран логи контейнера с именем pinger
- docker logs pinger

### Запустите второй раз контейнера с именем pinger 
- docker restart pinger

### Выведите на список всех контейнеров - запущенных и остановленных
- docker container ls -a

### Выведите на экран логи контейнера с именем pinger
- docker logs pinger

### Определите по логам общее количество запусков команды ping и какое общее количество отправленых запросов
- 2 запуска, 14 запросов

### Удалите контейнер с именем pinger
- docker container rm pinger

### Удалите образ busybox
- docker image rm busybox
