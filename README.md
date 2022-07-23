
# Домашнее задание к занятию "5.3. Введение. Экосистема. Архитектура. Жизненный цикл Docker контейнера"

## Как сдавать задания

Обязательными к выполнению являются задачи без указания звездочки. Их выполнение необходимо для получения зачета и диплома о профессиональной переподготовке.

Задачи со звездочкой (*) являются дополнительными задачами и/или задачами повышенной сложности. Они не являются обязательными к выполнению, но помогут вам глубже понять тему.

Домашнее задание выполните в файле readme.md в github репозитории. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.

Любые вопросы по решению задач задавайте в чате учебной группы.

---

## Задача 1

Сценарий выполения задачи:

- создайте свой репозиторий на https://hub.docker.com;
- выберете любой образ, который содержит веб-сервер Nginx;
- создайте свой fork образа;
- реализуйте функциональность:
запуск веб-сервера в фоне с индекс-страницей, содержащей HTML-код ниже:
```
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
```
Опубликуйте созданный форк в своем репозитории и предоставьте ответ в виде ссылки на https://hub.docker.com/username_repo.


Установим docker
```
vagrant@vagrant:~$ sudo mkdir -p /etc/apt/keyrings
vagrant@vagrant:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
vagrant@vagrant:~$ echo \
>   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
>   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
vagrant@vagrant:~$ sudo apt-get update
vagrant@vagrant:~$ sudo apt-get update
Hit:1 https://download.docker.com/linux/ubuntu focal InRelease
Err:2 https://apt.releases.hashicorp.com focal InRelease
  403  Forbidden [IP: 108.157.214.89 443]
Hit:3 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease
Hit:7 http://us.archive.ubuntu.com/ubuntu focal-security InRelease
Reading package lists... Done
E: Failed to fetch https://apt.releases.hashicorp.com/dists/focal/InRelease  403  Forbidden [IP: 108.157.214.89 443]
E: The repository 'https://apt.releases.hashicorp.com focal InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
vagrant@vagrant:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfile-basedir-perl libfile-desktopentry-perl libfile-mimeinfo-perl libfontenc1 libfwupdplugin1 libio-stringy-perl libipc-system-simple-perl libnet-dbus-perl libtie-ixhash-perl libu2f-udev
  libx11-protocol-perl libxft2 libxkbfile1 libxml-parser-perl libxml-twig-perl libxml-xpathengine-perl libxmuu1 libxv1 libxxf86dga1 linux-image-5.4.0-91-generic linux-modules-5.4.0-91-generic
  linux-modules-extra-5.4.0-91-generic x11-utils x11-xserver-utils xdg-utils
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  docker-ce-rootless-extras docker-scan-plugin pigz slirp4netns
Suggested packages:
  aufs-tools cgroupfs-mount | cgroup-lite
The following NEW packages will be installed:
  containerd.io docker-ce docker-ce-cli docker-ce-rootless-extras docker-compose-plugin docker-scan-plugin pigz slirp4netns
0 upgraded, 8 newly installed, 0 to remove and 17 not upgraded.
Need to get 108 MB of archives.
After this operation, 449 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 https://download.docker.com/linux/ubuntu focal/stable amd64 containerd.io amd64 1.6.6-1 [28.1 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 pigz amd64 2.4-1 [57.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 slirp4netns amd64 0.4.3-1 [74.3 kB]
Get:4 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce-cli amd64 5:20.10.17~3-0~ubuntu-focal [40.6 MB]
Get:5 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce amd64 5:20.10.17~3-0~ubuntu-focal [21.0 MB]
Get:6 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce-rootless-extras amd64 5:20.10.17~3-0~ubuntu-focal [8,171 kB]
Get:7 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-compose-plugin amd64 2.6.0~ubuntu-focal [6,560 kB]
Get:8 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-scan-plugin amd64 0.17.0~ubuntu-focal [3,521 kB]
Fetched 108 MB in 38s (2,818 kB/s)
Selecting previously unselected package pigz.
(Reading database ... 200926 files and directories currently installed.)
Preparing to unpack .../0-pigz_2.4-1_amd64.deb ...
Unpacking pigz (2.4-1) ...
Selecting previously unselected package containerd.io.
Preparing to unpack .../1-containerd.io_1.6.6-1_amd64.deb ...
Unpacking containerd.io (1.6.6-1) ...
Selecting previously unselected package docker-ce-cli.
Preparing to unpack .../2-docker-ce-cli_5%3a20.10.17~3-0~ubuntu-focal_amd64.deb ...
Unpacking docker-ce-cli (5:20.10.17~3-0~ubuntu-focal) ...
Selecting previously unselected package docker-ce.
Preparing to unpack .../3-docker-ce_5%3a20.10.17~3-0~ubuntu-focal_amd64.deb ...
Unpacking docker-ce (5:20.10.17~3-0~ubuntu-focal) ...
Selecting previously unselected package docker-ce-rootless-extras.
Preparing to unpack .../4-docker-ce-rootless-extras_5%3a20.10.17~3-0~ubuntu-focal_amd64.deb ...
Unpacking docker-ce-rootless-extras (5:20.10.17~3-0~ubuntu-focal) ...
Selecting previously unselected package docker-compose-plugin.
Preparing to unpack .../5-docker-compose-plugin_2.6.0~ubuntu-focal_amd64.deb ...
Unpacking docker-compose-plugin (2.6.0~ubuntu-focal) ...
Selecting previously unselected package docker-scan-plugin.
Preparing to unpack .../6-docker-scan-plugin_0.17.0~ubuntu-focal_amd64.deb ...
Unpacking docker-scan-plugin (0.17.0~ubuntu-focal) ...
Selecting previously unselected package slirp4netns.
Preparing to unpack .../7-slirp4netns_0.4.3-1_amd64.deb ...
Unpacking slirp4netns (0.4.3-1) ...
Setting up slirp4netns (0.4.3-1) ...
Setting up docker-scan-plugin (0.17.0~ubuntu-focal) ...
Setting up containerd.io (1.6.6-1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
Setting up docker-compose-plugin (2.6.0~ubuntu-focal) ...
Setting up docker-ce-cli (5:20.10.17~3-0~ubuntu-focal) ...
Setting up pigz (2.4-1) ...
Setting up docker-ce-rootless-extras (5:20.10.17~3-0~ubuntu-focal) ...
Setting up docker-ce (5:20.10.17~3-0~ubuntu-focal) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3.17) ...
```
проверим установленный докер
```
vagrant@vagrant:~$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

```
Получим image NGINX 
```
vagrant@vagrant:~$ sudo docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
461246efe0a7: Pull complete
a96aaf9a9ec3: Pull complete
650d8b758441: Pull complete
b138da793ac8: Pull complete
bb1705539683: Pull complete
b9ed43dcc388: Pull complete
Digest: sha256:db345982a2f2a4257c6f699a499feb1d79451a1305e8022f16456ddc3ad6b94c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

vagrant@vagrant:~$ sudo docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED      SIZE
nginx        latest    41b0e86104ba   3 days ago   142MB
```

Настройка конфигурации для Nginx сохраняем в файле execise1.conf


server {

        listen 81;

        server_name execise1.com;

        root /var/www/example1;

        index index.html;

        location / {

                try_files $uri $uri/ =404;

        }

}


Создаем простую web страницу в index.html

<html>
<head>
Hey, Netology
</head>
<body>
</body>
</html>" > index.html

Записываем dockerfile 

------взять из системы


vagrant@vagrant:~/docker$ sudo docker build -t kaplin-nginx:first_ver .
Sending build context to Docker daemon  6.144kB
Step 1/5 : FROM nginx
 ---> 41b0e86104ba
Step 2/5 : RUN  mkdir /var/www/
 ---> Running in 21d964dc686b
Removing intermediate container 21d964dc686b
 ---> 246e0f15f0b4
Step 3/5 : RUN  mkdir /var/www/execise1
 ---> Running in 82589d47fae6
Removing intermediate container 82589d47fae6
 ---> 55a8c580c479
Step 4/5 : COPY index.html /var/www/execise1
 ---> f2623c389e02
Step 5/5 : COPY execise1.conf /etc/nginx/conf.d
 ---> 4f4cb66b74a1
Successfully built 4f4cb66b74a1
Successfully tagged kaplin-nginx:first_ver

vagrant@vagrant:~/docker$ sudo docker images
REPOSITORY     TAG         IMAGE ID       CREATED          SIZE
kaplin-nginx   first_ver   4f4cb66b74a1   42 seconds ago   142MB
nginx          latest      41b0e86104ba   4 days ago       142MB
hello-world    latest      feb5d9fea6a5   9 months ago     13.3kB


vagrant@vagrant:~/docker$ sudo docker run kaplin-nginx:first_ver
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/07/17 01:50:39 [notice] 1#1: using the "epoll" event method
2022/07/17 01:50:39 [notice] 1#1: nginx/1.23.0
2022/07/17 01:50:39 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6)
2022/07/17 01:50:39 [notice] 1#1: OS: Linux 5.4.0-121-generic
2022/07/17 01:50:39 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/07/17 01:50:39 [notice] 1#1: start worker processes
2022/07/17 01:50:39 [notice] 1#1: start worker process 31
2022/07/17 01:50:39 [notice] 1#1: start worker process 32
2022/07/17 01:50:39 [notice] 1#1: start worker process 33
2022/07/17 01:50:39 [notice] 1#1: start worker process 34
2022/07/17 01:50:39 [notice] 1#1: start worker process 35
2022/07/17 01:50:39 [notice] 1#1: start worker process 36

vagrant@vagrant:~/docker$ sudo docker ps
CONTAINER ID   IMAGE                    COMMAND                  CREATED          STATUS          PORTS     NAMES
0dce3d5bd63b   kaplin-nginx:first_ver   "/docker-entrypoint.…"   16 seconds ago   Up 16 seconds   80/tcp    gifted_liskov
vagrant@vagrant:~/docker$ sudo docker exec -it 0dce3d5bd63b bash
root@0dce3d5bd63b:/# curl 0.0.0.0:81
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
root@0dce3d5bd63b:/#


sudo docker tag  kaplin-nginx:first_ver kapelman/05-virt-02-iaac:first-image

docker push kapelman/05-virt-02-iaac:tagname
docker push kapelman/05-virt-02-iaac:first-image


vagrant@vagrant:~/docker$ sudo docker tag  kaplin-nginx:first_ver kapelman/05-virt-02-iaac:first-image
vagrant@vagrant:~/docker$ sudo docker push kapelman/05-virt-02-iaac:first-image
The push refers to repository [docker.io/kapelman/05-virt-02-iaac]
faf347a7846e: Pushed
b4d767a203b7: Pushed
4aec14daed96: Pushed
a3e1ad034514: Pushed
de100bd247e0: Pushed
1d561d938628: Pushed
c03189a5ef70: Pushed
305b0db3a210: Pushed
1c99a7efe9d9: Pushed
43b3c4e3001c: Pushed
first-image: digest: sha256:4057cbd221ee4e1c4747ae5c2ee366319cee323e6e48dddadac9066bb42c8409 size: 2398


https://hub.docker.com/layers/258335888/kapelman/05-virt-02-iaac/first-image/images/sha256-4057cbd221ee4e1c4747ae5c2ee366319cee323e6e48dddadac9066bb42c8409?context=repo


## Задача 2

Посмотрите на сценарий ниже и ответьте на вопрос:
"Подходит ли в этом сценарии использование Docker контейнеров или лучше подойдет виртуальная машина, физическая машина? 
Может быть возможны разные варианты?"

Детально опишите и обоснуйте свой выбор.

--

Сценарий:

- Высоконагруженное монолитное java веб-приложение;
На мой взгляд лучше использовать виртуальную машину, в идеале, веделенный сервер, т.к. необходимо исключить влияние на аппаратные ресурсы хоста.
Нельзя допустить, что другие контейнеры при использовании Docker конкурировали за ресурсы с высоконагруженным приложением. 
- Nodejs веб-приложение; 
Вполне можно использовать Docker, т.к. нет специфичных требований, то вполне можно собрать все окружение в образ и запускать Nodejs приложение в Docker

- Мобильное приложение c версиями для Android и iOS;
Аналогичная история, можно использовать docker, тем более если мобильное приложение немонолитно и требуетя организовать взаимодействие для нескольких микросервисов 
(например, middle, backend, авторизация и т.д.). С помощью docker удобнее управлять таким приложением, разворачивать тестовые и разработческие среды, настраивать сетевые доступы и прочее.

- Шина данных на базе Apache Kafka;
Можно использовать докер, примеров настройки в инете достаточно. Единственное смущает: 1. Отказоустойчивость, отказал хост, на котором крутится Docker - 
шина перестала работать. В случае виртуальных машин или физических серверов отказоустойчивость в целом выше, если использовать несколько физически разных хостов.
Кроме того, при большой нагрузке не очень понятно, справится ли решение в docker с нагрузкой. 

- Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;
Elasticsearch рекомендуется устанавливать на выделенный физический сервер, чтобы не было конкуренции за ресурсы. Logstash и Kibana могут быть установлены в Docker, т.к. к ним 
нет таких требований. В целом же при невысокой критичности данного (всего лишь сбор и анализ логов), все продукты можно развернуть в Docker для более удобного разворачивания,
обновления версий, настройки сетевых соединений.

- Мониторинг-стек на базе Prometheus и Grafana;
- MongoDB, как основное хранилище данных для java-приложения;
- Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.

## Задача 3

- Запустите первый контейнер из образа ***centos*** c любым тэгом в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;
- Запустите второй контейнер из образа ***debian*** в фоновом режиме, подключив папку ```/data``` из текущей рабочей директории на хостовой машине в ```/data``` контейнера;
- Подключитесь к первому контейнеру с помощью ```docker exec``` и создайте текстовый файл любого содержания в ```/data```;
- Добавьте еще один файл в папку ```/data``` на хостовой машине;
- Подключитесь во второй контейнер и отобразите листинг и содержание файлов в ```/data``` контейнера.

## Задача 4 (*)

Воспроизвести практическую часть лекции самостоятельно.

Соберите Docker образ с Ansible, загрузите на Docker Hub и пришлите ссылку вместе с остальными ответами к задачам.


---

### Как cдавать задание

Выполненное домашнее задание пришлите ссылкой на .md-файл в вашем репозитории.

---
