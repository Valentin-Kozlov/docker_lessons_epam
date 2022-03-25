Задание:
========

Hometask: Написать Dockerfile для backend который располагается в директории /lib_catalog(для сборки контейнера необходимо использовать файл /lib_catalog/requirements.txt), для работы backend необходим postgresql, т.е. необходимо собрать 2 контейнера:
1. backend
2. postgresql

Осуществить сетевые настройки, для работы связки backend и postgresql

Решение:
========

1) Первым делом создадим сеть в режиме bridge для backend и database будущих контейнеров, следующей командой:


docker network create back-db -d bridge


2) Для запуска билда backend и database образов необходимо выполнить следующие команды из корневой директории:


docker build -t backend:latest -f ./lib_catalog/Dockerfile_backend .


docker build -t database:latest -f ./Dockerfile_database . 


3) Теперь мы можем запустить наши контейнеры используя созданную сеть для них и образы:


docker run --name backend --network back-db -p 8000:8000 -d backend:latest


docker run --name database --network frontend-backend-db -p 5432:5432 --env-file .env -d database:latest