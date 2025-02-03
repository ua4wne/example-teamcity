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

![build](./task2/build.png)

4. Поменяйте условия сборки: если сборка по ветке master, то должен происходит mvn clean deploy, иначе mvn clean test.

![condition](./task2/condition.png)

5. Для deploy будет необходимо загрузить [settings.xml](https://github.com/netology-code/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.

![upload](./task2/upload.png)
![select](./task2/select.png)

6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.

>Ответ: [pom.xml](/pom.xml)

7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

![artifact](./task2/artifact.png)

8. Мигрируйте build configuration в репозиторий.

![on_version](./task2/on_version.png)
![on_success](./task2/on_success.png)

9. Создайте отдельную ветку feature/add_reply в репозитории.

![new_branch](./task2/new_branch.png)

`git checkout feature/add_reply`

10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово hunter.

```
public String sayHunter(){
		return "Find hunter always";
	}
```

11. Дополните тест для нового метода на поиск слова hunter в новой реплике.

```
@Test
	public void welcomerSaysHunter() {
		assertThat(welcomer.sayHunter(), containsString("hunter"));
	}
```

12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
