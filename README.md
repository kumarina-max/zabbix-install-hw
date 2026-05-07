markdown
# zabbix-install-hw
# Домашнее задание к занятию «Система мониторинга Zabbix» Кукушкина Марина

# Задание 1
В рамках домашнего задания был установлен Zabbix Server 7.0 с поддержкой PostgreSQL и веб-интерфейсом на базе Apache. Установка производилась на виртуальную машину Debian 11 в Yandex Cloud

# Все использованные команды для установки
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y postgresql postgresql-contrib

wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb
dpkg -i zabbix-release_latest_6.0+debian11_all.deb
sudo apt update

sudo apt install -y zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts 

sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

sudo nano /etc/zabbix/zabbix_server.conf  # Установка DBPassword

sudo systemctl restart zabbix-server apache2
sudo systemctl enable zabbix-server  apache2

## Результат установки

### Скриншот авторизации в веб-интерфейсе Zabbix


![Страница авторизации](https://github.com/kumarina-max/zabbix-install-hw/blob/main/screenshots/%20zabbix-login.png)
 
