# Домашнее задание к занятию 12 «GitLab»

## Подготовка к выполнению


1. Или подготовьте к работе Managed GitLab от yandex cloud [по инструкции](https://cloud.yandex.ru/docs/managed-gitlab/operations/instance/instance-create) .
Или создайте виртуальную машину из публичного образа [по инструкции](https://cloud.yandex.ru/marketplace/products/yc/gitlab ) .
2. Создайте виртуальную машину и установите на нее gitlab runner, подключите к вашему серверу gitlab  [по инструкции](https://docs.gitlab.com/runner/install/linux-repository.html) .

3. (* Необязательное задание повышенной сложности. )  Если вы уже знакомы с k8s попробуйте выполнить задание, запустив gitlab server и gitlab runner в k8s  [по инструкции](https://cloud.yandex.ru/docs/tutorials/infrastructure-management/gitlab-containers). 

4. Создайте свой новый проект.
5. Создайте новый репозиторий в GitLab, наполните его [файлами](./repository).
6. Проект должен быть публичным, остальные настройки по желанию.

## Основная часть

### DevOps

В репозитории содержится код проекта на Python. Проект — RESTful API сервис. Ваша задача — автоматизировать сборку образа с выполнением python-скрипта:

1. Образ собирается на основе [centos:7](https://hub.docker.com/_/centos?tab=tags&page=1&ordering=last_updated).
2. Python версии не ниже 3.7.
3. Установлены зависимости: `flask` `flask-jsonpify` `flask-restful`.
4. Создана директория `/python_api`.
5. Скрипт из репозитория размещён в /python_api.
6. Точка вызова: запуск скрипта.
7. При комите в любую ветку должен собираться docker image с форматом имени hello:gitlab-$CI_COMMIT_SHORT_SHA . Образ должен быть выложен в Gitlab registry или yandex registry.

<details><summary>Лог</summary>
  
```bash
Running with gitlab-runner 16.7.0 (102c81ba)
  on Ubuntu VXsxPufmP, system ID: s_b19d5bbfc5fd
Preparing the "docker" executor
00:39
Using Docker executor with image docker:20.10.5 ...
Starting service docker:20.10.5-dind ...
Authenticating with credentials from /root/.docker/config.json
Pulling docker image docker:20.10.5-dind ...
Using docker image sha256:0a9822c8848df3eb0a1562e553fdd54215939ef0a528434ee026c64ff645148c for docker:20.10.5-dind with digest docker@sha256:e4ecd4e9ad5140d584669451b05e406d8cf7603e51972b862178ad93c38b2b08 ...
Waiting for services to be up and running (timeout 30 seconds)...
*** WARNING: Service runner-vxsxpufmp-project-1-concurrent-0-d7ff792a052c4982-docker-0 probably didn't start properly.
Health check error:
service "runner-vxsxpufmp-project-1-concurrent-0-d7ff792a052c4982-docker-0-wait-for-service" timeout
Health check container logs:
2023-12-23T21:59:16.465159368Z waiting for TCP connection to 172.17.0.4 on [2375 2376]...
2023-12-23T21:59:16.465211861Z dialing 172.17.0.4:2376...
2023-12-23T21:59:16.465385896Z dialing 172.17.0.4:2375...
2023-12-23T21:59:17.472630571Z dialing 172.17.0.4:2375...
2023-12-23T21:59:17.472663653Z dialing 172.17.0.4:2376...
Service container logs:
2023-12-23T21:59:15.627770950Z Generating RSA private key, 4096 bit long modulus (2 primes)
2023-12-23T21:59:15.769992553Z ....................................................++++
2023-12-23T21:59:15.911550673Z .....................................................++++
2023-12-23T21:59:15.911769883Z e is 65537 (0x010001)
2023-12-23T21:59:15.921652459Z Generating RSA private key, 4096 bit long modulus (2 primes)
2023-12-23T21:59:16.060403765Z ....................................................++++
2023-12-23T21:59:16.165978856Z ......................................++++
2023-12-23T21:59:16.166186173Z e is 65537 (0x010001)
2023-12-23T21:59:16.183817440Z Signature ok
2023-12-23T21:59:16.183829863Z subject=CN = docker:dind server
2023-12-23T21:59:16.183938646Z Getting CA Private Key
2023-12-23T21:59:16.199780541Z /certs/server/cert.pem: OK
2023-12-23T21:59:16.202034788Z Generating RSA private key, 4096 bit long modulus (2 primes)
2023-12-23T21:59:16.299155228Z .................................++++
2023-12-23T21:59:16.428857223Z ................................................++++
2023-12-23T21:59:16.429096409Z e is 65537 (0x010001)
2023-12-23T21:59:16.444864686Z Signature ok
2023-12-23T21:59:16.445014486Z subject=CN = docker:dind client
2023-12-23T21:59:16.445177269Z Getting CA Private Key
2023-12-23T21:59:16.453889835Z /certs/client/cert.pem: OK
2023-12-23T21:59:16.455992750Z mount: permission denied (are you root?)
2023-12-23T21:59:16.456073501Z Could not mount /sys/kernel/security.
2023-12-23T21:59:16.456079001Z AppArmor detection and --privileged mode might break.
2023-12-23T21:59:16.456897510Z mount: permission denied (are you root?)
*********
Authenticating with credentials from /root/.docker/config.json
Pulling docker image docker:20.10.5 ...
Using docker image sha256:1588477122de4fdfe9fcb9ddeeee6ac6b93e9e05a65c68a6e22add0a98b8e0fe for docker:20.10.5 with digest docker@sha256:7ed427295687586039ff3433bb9b4419c5cf1e6294025dadf7641126665a78f5 ...
Preparing environment
00:01
Running on runner-vxsxpufmp-project-1-concurrent-0 via UbuntaTEST...
Getting source from Git repository
00:01
Fetching changes with git depth set to 20...
Reinitialized existing Git repository in /builds/fe1br0/netology/.git/
Checking out 653b242e as detached HEAD (ref is main)...
Skipping Git submodules setup
Executing "step_script" stage of the job script
00:33
Using docker image sha256:1588477122de4fdfe9fcb9ddeeee6ac6b93e9e05a65c68a6e22add0a98b8e0fe for docker:20.10.5 with digest docker@sha256:7ed427295687586039ff3433bb9b4419c5cf1e6294025dadf7641126665a78f5 ...
$ docker build -t $CI_REGISTRY/fe1br0/netology/app:latest .
Step 1/6 : FROM centos:7
 ---> eeb6ee3f44bd
Step 2/6 : RUN yum install python3 python3-pip -y
 ---> Using cache
 ---> 1d4b65c1fce9
Step 3/6 : COPY requirements.txt requirements.txt
 ---> Using cache
 ---> 12c4f988c705
Step 4/6 : RUN pip3 install -r requirements.txt
 ---> Using cache
 ---> 7df4a54c89b8
Step 5/6 : COPY app.py app.py
 ---> Using cache
 ---> 056fc49620b6
Step 6/6 : CMD ["python3", "app.py"]
 ---> Using cache
 ---> 8a8b85457653
Successfully built 8a8b85457653
Successfully tagged fe1br0.gitlab.yandexcloud.net:5050/fe1br0/netology/app:latest
$ docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" $CI_REGISTRY
WARNING! Using --password via the CLI is insecure. Use --password-stdin.
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store
Login Succeeded
$ docker push $CI_REGISTRY/fe1br0/netology/app:latest
The push refers to repository [fe1br0.gitlab.yandexcloud.net:5050/fe1br0/netology/app]
dda9971df7d9: Preparing
868508c12858: Preparing
3a248ff23bcb: Preparing
24f55a1764e4: Preparing
174f56854903: Preparing
3a248ff23bcb: Pushed
dda9971df7d9: Pushed
868508c12858: Pushed
174f56854903: Pushed
24f55a1764e4: Pushed
latest: digest: sha256:517fb7a640ebceea773e9d2f086c0e2c6403585912742140eb7dd66cc55ce0b5 size: 1366
Cleaning up project directory and file based variables
00:01
Job succeeded
```
</details>

![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/c9436cda-9d79-4e3c-898d-f1ead48eed76)


### Product Owner

Вашему проекту нужна бизнесовая доработка: нужно поменять JSON ответа на вызов метода GET `/rest/api/get_info`, необходимо создать Issue в котором указать:

1. Какой метод необходимо исправить.
2. Текст с `{ "message": "Already started" }` на `{ "message": "Running"}`.
3. Issue поставить label: feature.

```Выполнено```
![Screenshot_5](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/c49e1b10-a8b4-4880-bbab-f82d7ebd95df)

![Screenshot_1](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/841dd36d-d28e-4bd0-b550-4258ff451d41)



### Developer

Пришёл новый Issue на доработку, вам нужно:

1. Создать отдельную ветку, связанную с этим Issue.
2. Внести изменения по тексту из задания.
3. Подготовить Merge Request, влить необходимые изменения в `master`, проверить, что сборка прошла успешно.


![Screenshot_2](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/9e82b421-4706-4e94-a90a-c9f15015ce66)



### Tester

Разработчики выполнили новый Issue, необходимо проверить валидность изменений:

1. Поднять докер-контейнер с образом `python-api:latest` и проверить возврат метода на корректность.
2. Закрыть Issue с комментарием об успешности прохождения, указав желаемый результат и фактически достигнутый.

![Screenshot_4](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/ed7f526a-3e16-46e2-8a66-2775c6e81a22)

![Screenshot_6](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/aada360f-9431-46f2-aab4-92d2a950fcc4)


## Итог

В качестве ответа пришлите подробные скриншоты по каждому пункту задания:

- файл gitlab-ci.yml; 
- Dockerfile; 
- лог успешного выполнения пайплайна;
- решённый Issue.

### Важно 
После выполнения задания выключите и удалите все задействованные ресурсы в Yandex Cloud.

