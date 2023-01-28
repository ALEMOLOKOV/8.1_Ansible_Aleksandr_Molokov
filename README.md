# 8.1_Ansible_Aleksandr_Molokov

## Подготовка к выполнению
1. Установите ansible версии 2.10 или выше.
2. Создайте свой собственный публичный репозиторий на github с произвольным именем.
3. Скачайте [playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.

## Основная часть

1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте какое значение имеет факт `some_fact` для указанного хоста при выполнении playbook'a.

## Ответ
Запуск playbook
ansible-playbook -i inventory/test.yml site.yml
Факт some_fact имеет значение 12
![Задание 1](https://user-images.githubusercontent.com/109212419/215259678-eed628fa-63fb-442b-b48e-10e6e6b96569.jpg)

2. Найдите файл с переменными (group_vars) в котором задаётся найденное в первом пункте значение и поменяйте его на 'all default fact'.

## Ответ
Меняем значение

![Задание 2](https://user-images.githubusercontent.com/109212419/215259836-3f416bc5-42bf-4ec4-ac5d-b745ddfaba35.jpg)

3. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.

## Ответ
Подготовка окружения через docker-compose

![Задание 3](https://user-images.githubusercontent.com/109212419/215259863-e798a717-7640-40be-b45d-43352226bfcc.jpg)

4. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.

## Ответ
Запуск  playbook на окружении из `prod.yml` 
some_fact для Centos7 - el, some_fact для ubunto - deb

![Задание 4](https://user-images.githubusercontent.com/109212419/215259956-3b4b11fc-7da1-4a13-a4aa-8b75a8f7e957.jpg)

5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились следующие значения: для `deb` - 'deb default fact', для `el` - 'el default fact'.

## Ответ
Новые значения some_fact

![Задание 5 1](https://user-images.githubusercontent.com/109212419/215260026-11d36008-8a6c-45fa-bbe5-78530aaf7082.jpg)

![Задание 5 2](https://user-images.githubusercontent.com/109212419/215260035-3d06187b-9663-4134-829f-e873b4d57959.jpg)

6.  Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.

## Ответ
Повторный запуск playbook

![Задание 6](https://user-images.githubusercontent.com/109212419/215260056-acb9e7d5-f4fd-4d8c-a5a2-6a2a20089df3.jpg)

7. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`.

## Ответ
Шифрование фактов, пароль netology

![Задание 7](https://user-images.githubusercontent.com/109212419/215260081-0b013f19-13ba-405b-81fe-0f32f2887c51.jpg)

8. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности.

## Ответ
Запуск playbook с ключом --ask-vault-pass

![Задание 8](https://user-images.githubusercontent.com/109212419/215260111-7ccb4a77-50d6-4aaf-84fd-498f051a00f4.jpg)

9. Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.

## Ответ
Посмотреть список плагинов можно с помощью команды ansible-doc -t connection -l. 
Для работы на `control node` подходит local

![задание 9](https://user-images.githubusercontent.com/109212419/215260177-fcd43d2b-01e8-440d-9a0d-d04e46fa2837.jpg)

10. В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения.

## Ответ
Добавление новой группы хостов

![Задание 10](https://user-images.githubusercontent.com/109212419/215260253-88561c44-137d-4c81-ad8c-98fd311cceec.jpg)

11. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь что факты `some_fact` для каждого из хостов определены из верных `group_vars`.

## Ответ
Запуск playbook

![задание 11](https://user-images.githubusercontent.com/109212419/215260316-dbb2cd5d-c081-44b6-a629-49c1bd339356.jpg)

12. Заполните `README.md` ответами на вопросы. Сделайте `git push` в ветку `master`. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым `playbook` и заполненным `README.md`.
