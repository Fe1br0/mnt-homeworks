# Домашнее задание к занятию 9 «Процессы CI/CD»

## Подготовка к выполнению

1. Создайте два VM в Yandex Cloud с параметрами: 2CPU 4RAM Centos7 (остальное по минимальным требованиям).
2. Пропишите в [inventory](./infrastructure/inventory/cicd/hosts.yml) [playbook](./infrastructure/site.yml) созданные хосты.
3. Добавьте в [files](./infrastructure/files/) файл со своим публичным ключом (id_rsa.pub). Если ключ называется иначе — найдите таску в плейбуке, которая использует id_rsa.pub имя, и исправьте на своё.
4. Запустите playbook, ожидайте успешного завершения.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/7339a9c5-a7f6-4e24-aad6-38ca12bd2af6)

5. Проверьте готовность SonarQube через [браузер](http://localhost:9000).

![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/8cf00f9c-8b66-4513-9fe6-9bd02c8aef74)

6. Зайдите под admin\admin, поменяйте пароль на свой.
7.  Проверьте готовность Nexus через [бразуер](http://localhost:8081).
8. Подключитесь под admin\admin123, поменяйте пароль, сохраните анонимный доступ.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/0b20bb8f-380e-48e5-98af-037480aca218)

## Знакомоство с SonarQube

### Основная часть

1. Создайте новый проект, название произвольное.
2. Скачайте пакет sonar-scanner, который вам предлагает скачать SonarQube.
3. Сделайте так, чтобы binary был доступен через вызов в shell (или поменяйте переменную PATH, или любой другой, удобный вам способ).
4. Проверьте `sonar-scanner --version`.

![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/d904330f-71c7-4eb2-be19-67b77a42cafa)

6. Запустите анализатор против кода из директории [example](./example) с дополнительным ключом `-Dsonar.coverage.exclusions=fail.py`.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/bf402167-4564-4efa-9058-df07c80faffb)

7. Посмотрите результат в интерфейсе.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/accdd796-5f86-4c42-9e15-55f97c3f7240)

8. Исправьте ошибки, которые он выявил, включая warnings.
9. Запустите анализатор повторно — проверьте, что QG пройдены успешно.
10. Сделайте скриншот успешного прохождения анализа, приложите к решению ДЗ.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/76bc1f6c-a32b-4989-b65f-cecd4babff40)

![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/be72ea43-9db0-4a50-9e79-4cd7dbb7ed2d)


## Знакомство с Nexus

### Основная часть

1. В репозиторий `maven-public` загрузите артефакт с GAV-параметрами:

 *    groupId: netology;
 *    artifactId: java;
 *    version: 8_282;
 *    classifier: distrib;
 *    type: tar.gz.

![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/ebb61f28-4177-4a96-97c1-1ff515dc8523)

   
2. В него же загрузите такой же артефакт, но с version: 8_102.
3. Проверьте, что все файлы загрузились успешно.
4. В ответе пришлите файл `maven-metadata.xml` для этого артефекта.
```xml
<metadata modelVersion="1.1.0">
<groupId>netology</groupId>
<artifactId>java</artifactId>
<versioning>
<latest>8_282</latest>
<release>8_282</release>
<versions>
<version>8_102</version>
<version>8_282</version>
</versions>
<lastUpdated>20231219151623</lastUpdated>
</versioning>
</metadata>
```
### Знакомство с Maven

### Подготовка к выполнению

1. Скачайте дистрибутив с [maven](https://maven.apache.org/download.cgi).
2. Разархивируйте, сделайте так, чтобы binary был доступен через вызов в shell (или поменяйте переменную PATH, или любой другой, удобный вам способ).
3. Удалите из `apache-maven-<version>/conf/settings.xml` упоминание о правиле, отвергающем HTTP- соединение — раздел mirrors —> id: my-repository-http-unblocker.
4. Проверьте `mvn --version`.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/3d9d07fd-53c3-43c8-92f4-4ad0dd7b3424)

5. Заберите директорию [mvn](./mvn) с pom.

### Основная часть

1. Поменяйте в `pom.xml` блок с зависимостями под ваш артефакт из первого пункта задания для Nexus (java с версией 8_282).
2. Запустите команду `mvn package` в директории с `pom.xml`, ожидайте успешного окончания.
3. Проверьте директорию `~/.m2/repository/`, найдите ваш артефакт.
4. В ответе пришлите исправленный файл `pom.xml`.
![image](https://github.com/Fe1br0/mnt-homeworks/assets/106814458/4ffc3ae8-bbab-4100-bb12-acf57eee83bc)

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
