## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа jetbrains/teamcity-server.

![server](./task1/server.png)

2. Дождитесь запуска teamcity, выполните первоначальную настройку.

![install](./task1/install.png)
![setup](./task1/setup.png)

3. Создайте ещё один инстанс (2CPU4RAM) на основе образа jetbrains/teamcity-agent. Пропишите к нему переменную окружения SERVER_URL: "http://<teamcity_url>:8111".

![agent](./task1/agent.png)

4. Авторизуйте агент.

![auth](./task1/auth.png)

5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).

6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure/site.yml).

![nexus](./task1/nexus.png)
![play](./task1/play.png)

## Основная часть

1. Создайте новый проект в teamcity на основе fork.

![create](./task2/create.png)

2. Сделайте autodetect конфигурации.

![autodetect](./task2/autodetect.png)

3. Сохраните необходимые шаги, запустите первую сборку master.