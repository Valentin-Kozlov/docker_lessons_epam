Задание:
========
Hometask: Написать Dockerfile для frontend располагается в директории /frontend, собрать и запустить.

1) Перейти в директрорию frontend;

2) Запустить билд имеджа для frontend:


docker build -t frontend:latest -f .\Dockerfile_frontend .


3) Для запуска контейнера frontend выполнить следующую команду:


docker run --name frontend -p 80:80 -d frontend:latest