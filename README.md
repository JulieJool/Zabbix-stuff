# Zabbix-stuff

### Задание 1

![Скриншот успешной установки zabbix](https://github.com/JulieJool/zabbix-stuff/blob/main/img/zabbix-installation.jpg)

![Скриншот авторизации в админке zabbix](https://github.com/JulieJool/zabbix-stuff/blob/main/img/zabbix-global-view.jpg)

Прежде необходимо установить PostgreSQL:  
sudo apt install postgresql postgresql-contrib  
sudo systemctl status postgresql  

Затем - zabbix:  
`wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb`  
`apt update`  
`apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`  
`sudo -u postgres createuser --pwprompt zabbix`  
`sudo -u postgres createdb -O zabbix zabbix`  
`zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`  
`sudo nano /etc/zabbix/zabbix_server.conf`  
Замена DBPassword=password на заданный пароль  
`systemctl restart zabbix-server zabbix-agent apache2`  
`systemctl enable zabbix-server zabbix-agent apache2`  
