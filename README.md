CSF
=========

установка CSF из исходников, на любую ОС, с вашей конфигурацией.

Зависимости
------------

исходники csf, должны у вас распологатся в /roles/csf/files/csf.tgz
Скачать исходники в папку вы можете этой коммандой

```bash

cd /roles/csf/files/csf.tgz && wget https://download.configserver.com/csf.tgz

```

Переменные роли
---------------
cat roles/csf/vars/csf_settings.yml
```yaml
---

# download Url csf
csf_url: "https://download.configserver.com/csf.tgz"

# Allow incoming TCP ports
TCP_IN: "20,21,22,25,53,80,110,143,443,465,587,993,995"

# Allow outgoing TCP ports
TCP_OUT:  "20,21,22,25,53,80,110,113,443,587,993,995"

# Allow incoming UDP ports
UDP_IN: "20,21,53,80,443"

# To allow outgoing traceroute add 33434:33523 to this list
UDP_OUT: "20,21,53,113,123"

# Allow incoming PING. Disabling PING will likely break external uptime
ICMP_IN: "1"

# ipv6 enable 1 disable 0
IPV6: "0"

# These changes are not necessary if the SPI firewall is used
IPV6_SPI: "1"

# Allow incoming IPv6 TCP ports
TCP6_IN: "20,21,22,25,53,80,110,143,443,465,587,993,995"

# Allow outgoing IPv6 TCP ports
TCP6_OUT: "20,21,22,25,53,80,110,113,443,587,993,995"

# Allow incoming IPv6 UDP ports
UDP6_IN: "20,21,53,80,443"

# Allow outgoing IPv6 UDP ports
# To allow outgoing traceroute add 33434:33523 to this list

UDP6_OUT: "20,21,53,113,123"

```

Зависимости роли
----------------

У роли нет каких либо зависимостей

Пример Playbook
----------------

Простой плэйбук запуска роли csf (какие либо параметры роль не принимает)

```yaml
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
