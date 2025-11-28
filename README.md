# Домашнее задание к занятию «`Система мониторинга Zabbix`» - `Игонин В.А.`

### Задание 1
Установите Zabbix Server с веб-интерфейсом.

**Процесс выполнения**
  Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
  Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
  Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
  Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
  Требования к результатам
  Прикрепите в файл README.md скриншот авторизации в админке.
  Приложите в файл README.md текст использованных команд в GitHub.

### Решение 1
<details> 

![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/1.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/1.2.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/1.3.png)

**Список всех использованных команд:**
apt update
apt install postgresql
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
dpkg -i zabbix-release_latest_6.0+debian11_all.deb
ls -la /etc/apt/sources.list.d/
apt update
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent
systemctl status zabbix-server
su - postgres -c 'psql --command "CREATE USER zabbix WITH PASSWORD '\'123456789\'';"'
su - postgres -c 'psql --command "CREATE DATABASE zabbix OWNER zabbix;"'
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
nano /etc/zabbix/zabbix_server.conf
systemctl restart zabbix-server zabbix-agent apache2
systemctl enable zabbix-server zabbix-agent apache2

</details> 
  
### Задание 2
Установите Zabbix Agent на два хоста.

**Процесс выполнения**
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.
Требования к результатам
Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Приложите в файл README.md текст использованных команд в GitHub

### Решение 2
<details> 

![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/2.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/2.1.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/2.2.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/2.3.png)

**Список всех использованных команд:**
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
dpkg -i zabbix-release_latest_6.0+debian11_all.deb
apt update
apt install zabbix-agent
systemctl restart zabbix-agent
systemctl enable zabbix-agent
nano /etc/zabbix/zabbix_agentd.conf
tail -f /var/log/zabbix/zabbix_agentd.log
systemctl restart zabbix-agent.service
systemctl status zabbix-agent.service
tail -f /var/log/zabbix/zabbix_agentd.log
</details>

### Задание 3 со звёздочкой*
Установите Zabbix Agent на Windows (компьютер) и подключите его к серверу Zabbix.

Требования к результатам
Приложите в файл README.md скриншот раздела Latest Data, где видно свободное место на диске C:

### Решение 3

![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/3.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/3.1.png)
![alt text](https://github.com/Sayward-k8/smon-hw-02/blob/main/image/3.2.png)

<details>

</details>

