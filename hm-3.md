## Задание 3 - Volumes

Используя Docker CLI выполните следующие действия:

1. Загрузите образ node версии 15.14
- docker pull node:15.14
```
15.14: Pulling from library/node
bfde2ec33fbc: Pull complete
787f5e2f1047: Pull complete
7b6173a10eb8: Pull complete
dc05be471d51: Pull complete
55fab5cadd3c: Pull complete
bd821d20ef8c: Pull complete
6041b69671c6: Pull complete
989c5d2d2313: Pull complete
4b57d41e8391: Pull complete
Digest: sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Status: Downloaded newer image for node:15.14
docker.io/library/node:15.14
```

2. Запустите контейнер с именем `first_node` из образа node версии 15.14 в фоновом режиме, подключив папку `data` из текущей директории в `/var/first/data` контейнера
- docker run -d -t -v data:/var/first/data --name first_node node:15.14
```
1795b4dd5c897f3fc5904a61d26b7735956b41ab3869ffaf4f98594355ef752e
```

3. Запустите контейнер с именем `second_node` из образа node версии 15.14 в фоновом режиме, подключив папку `data` из текущей директории в `/var/second/data` контейнера
-  docker run -d -t -v data:/var/second/data --name second_node node:15.14
```
ac79f4361f11bf71cb4c1f68b277306253059cd7d825fa7a139aebc795f41442
```

4. Подключитесь к контейнеру `first_node` с помощью exec и создайте текстовый файл любого содержания в `/var/first/data`
- docker exec -it first_node bash
- cd var/first/data
- echo "insert text here" > myfile.txt

5. Добавьте еще один файл в папку `data` на хостовой машине
- echo "another text here" > myfile2.txt

6. Подключитесь к контейнеру `second_node` с помощью `exec` и получите список файлов в директории `/var/second/data`, выведете на экран содержимое файлов
- docker exec -it second_node bash
- cd var/second/data
- ls -l
```
total 8
-rw-r--r-- 1 root root 17 Nov  2 11:08 myfile.txt
-rw-r--r-- 1 root root 18 Nov  2 11:11 myfile2.txt
```
- cat myfile.txt
``` 
insert text here
```
- cat myfile2.txt
``` 
another text here
```

7. Остановите оба контейнера
- docker stop first_node
- docker stop second_node

8. Удалите оба контейнера
- docker container rm first_node
- docker container rm second_node

9. Удалите образ node версии 15.14
- docker image rm node:15.14
```
Untagged: node:15.14
Untagged: node@sha256:608bba799613b1ebf754034ae008849ba51e88b23271412427b76d60ae0d0627
Deleted: sha256:3d3f41722daf1a77c34d6eade6676bbffa2d6a2a21095de2ab0c427a5c942fc9
Deleted: sha256:601382991a159cfc5013ad973158f30b7b7a913e8d7e547b3456deab3ad98022
Deleted: sha256:d5db49eecae8c02c9ea3a79f89c43ded9162bac118a0302a7b514d0df82aa112
Deleted: sha256:a2c1973858d0aad3de0927294602b17c8ef9050c30e0f461e0868997a08552a4
Deleted: sha256:a0153172017a08a521a8be971ca4dcb5fbc4b7227642c12bbb2da6265bd66b50
Deleted: sha256:f1123940e954d335d91b52a40fab4f8144f38ff113ade7d65663071d0f06da6f
Deleted: sha256:f1f4fbb0e7e6e0ce2d9eae1e577f9f6df0a719dd874bff00b2d08895c75c297d
Deleted: sha256:1eb455ab6d45fdbbd90fccff791ffa228080c052acf464f8da1b1d78650bd706
Deleted: sha256:1dbe832a694971a925d7d216f49b700c95f402bd72288f9d37eceb1d59dcf72d
Deleted: sha256:2f4ee6a2e1b5dfb9236cd262e788f9d39109242ca27a4aacb583c8af66ec3ff7
```
