# Домашнее задание к занятию 1 «Введение в Ansible»

## Подготовка к выполнению

1. Установите Ansible версии 2.10 или выше.
2. Создайте свой публичный репозиторий на GitHub с произвольным именем.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.

## Основная часть

1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте значение, которое имеет факт `some_fact` для указанного хоста при выполнении playbook.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/ee909aad-7dde-4616-ae4f-8d3e6f5b9554)

2. Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на `all default fact`.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/d468443b-7df8-4b99-8962-d5d0ee07bc7e)


3. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/e3846d90-04a6-4946-87a2-bd0f490418dc)

4. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/ef9307bd-ae3b-4bb7-9433-a61ba761fab1)

- Значение `some_fact` для `managed host` "ubuntu" `deb`.
- Значение `some_fact` для `managed host` "centos7" `el`.

5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились значения: для `deb` — `deb default fact`, для `el` — `el default fact`.
6. Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/b385be8f-9b46-4f23-9bbe-744b665a0370)

- Значение `some_fact` для `managed host` "ubuntu" `deb default fact`.
- Значение `some_fact` для `managed host` "centos7" `el default fact`.

7. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/1a8cad26-d25f-4438-a9ee-4ff4ef97b2e3)

8. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/e7cec239-8fbf-4627-8486-c816a870059e)

9. Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/db25c023-2bb1-4d94-a9d3-f58888d67a12)

Для подключения к `control node` используется плагин `local`

10. В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/ec7d7fa9-ddbb-439e-94c8-6fd485cbabb0)

11. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь, что факты `some_fact` для каждого из хостов определены из верных `group_vars`.

![image](https://github.com/grifin01/mnt-homeworks/assets/111656372/aed46cea-8bce-47b8-9874-24106aca1f78)

- Значение `some_fact` для `managed host` "ubuntu" `deb default fact`.
- Значение `some_fact` для `managed host` "centos7" `el default fact`.
- Значение `some_fact` для `managed host` "localhost" `all default fact`.

12. Заполните `README.md` ответами на вопросы. Сделайте `git push` в ветку `master`. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым `playbook` и заполненным `README.md`.
13. Предоставьте скриншоты результатов запуска команд.

## Необязательная часть

1. При помощи `ansible-vault` расшифруйте все зашифрованные файлы с переменными.
2. Зашифруйте отдельное значение `PaSSw0rd` для переменной `some_fact` паролем `netology`. Добавьте полученное значение в `group_vars/all/exmp.yml`.
3. Запустите `playbook`, убедитесь, что для нужных хостов применился новый `fact`.
4. Добавьте новую группу хостов `fedora`, самостоятельно придумайте для неё переменную. В качестве образа можно использовать [этот вариант](https://hub.docker.com/r/pycontribs/fedora).
5. Напишите скрипт на bash: автоматизируйте поднятие необходимых контейнеров, запуск ansible-playbook и остановку контейнеров.
6. Все изменения должны быть зафиксированы и отправлены в ваш личный репозиторий.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
