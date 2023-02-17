Имя Роли
=========

csf - установка роли из исходников, на любую ОС, а также конфигурация csf, по вашему усмотрению из vars

Зависимости
------------

исходники csf, должны у вас распологатся в имя_роли/files/csf.tgz
Скачать исходники в папку вы можете этой коммандой

```bash

  cd имя_роли/files/csf.tgz && wget https://download.configserver.com/csf.tgz

```

Переменные роли
---------------

В роли переменные которые вы зохотите изменить находятся по пути /roles/csf/vars/csf_settings.yml
в файле прописаны меременный для файла csf.conf в template, только те  переменные которыч требуется частое изменение.

Зависимости роли
----------------

У роли нет каких либо зависимостей

Пример Playbook
----------------

Простой плэйбук запуска роли csf (какие либо параметры роль не принимает)

```bash
        ---

        - hosts: 127.0.0.1
          become: yes

          roles:
           - csf

```

Пример запуска роли с тегами
----------------------------

в роли доступны теги

```bash
csf            # запуск всех тасков кроме csf_enable csf_disable
csf_install    # установка запуск csf
csf_configure  # копирования конфига из template с переменными в vars в директорию csf, перезапуск csf
csf_enable     # запуск csf
csf_disable    # остановка csf
```

```bash
# запустить все таски кроме csf_enable csf_disable
ansible-playbook csf.yaml
# запустить все таски кроме csf_enable csf_disable
ansible-playbook csf.yaml --tags="csf"
# запустить только установку и конфигурацию
ansible-playbook csf.yaml --tags="csf_install, csf_configure"
```

License
-------

BSD

Author Information
------------------

Solomatin Anton
