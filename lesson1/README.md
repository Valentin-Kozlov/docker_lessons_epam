Задание:
========
Hometask: Написать Dockerfile для frontend располагается в директории /frontend, собрать и запустить.

Решение:
========
1) Перейти в директорию frontend;

2) Запустить билд имеджа для frontend:

``` docker build -t frontend:latest -f ./frontend/Dockerfile_frontend . ```

3) Для запуска контейнера frontend выполнить следующую команду:

``` docker run --name frontend -p 80:80 -d frontend:latest ```
