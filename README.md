# zabbix-p.1

### Задание 1

![Скриншот успешной установки zabbix](https://github.com/JulieJool/zabbix-stuff/blob/main/img/zabbix-installation.jpg)

![Скриншот авторизации в админке zabbix](https://github.com/JulieJool/zabbix-stuff/blob/main/img/zabbix-global-view.jpg)

Прежде необходимо установить PostgreSQL:  
`sudo apt install postgresql postgresql-contrib`  
`sudo systemctl status postgresql`  

Затем - zabbix:  
`wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb`  
`pkg -i zabbix-release_6.0-4+debian11_all.deb`  
`apt update`  
`apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`  
`sudo -u postgres createuser --pwprompt zabbix`  
`sudo -u postgres createdb -O zabbix zabbix`  
`zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`  
`sudo nano /etc/zabbix/zabbix_server.conf`  
*Замена DBPassword=password на заданный пароль*  
`systemctl restart zabbix-server zabbix-agent apache2`  
`systemctl enable zabbix-server zabbix-agent apache2`  


# Задание 2

Скриншот раздела Configuration > Hosts:
![Скриншот раздела Configuration > Hosts](https://github.com/JulieJool/zabbix-stuff/blob/main/img/Configuration-hosts.png)

Скриншоты лога zabbix agent-ов:
![Скриншоты лога zabbix agent-ов](https://github.com/JulieJool/zabbix-stuff/blob/main/img/log-agent-1.png)

![Скриншоты лога zabbix agent-ов](https://github.com/JulieJool/zabbix-stuff/blob/main/img/log-agent-2.png)

Cкриншот раздела Monitoring > Latest data для обоих хостов:
![Cкриншот раздела Monitoring > Latest data для обоих хостов](https://github.com/JulieJool/zabbix-stuff/blob/main/img/Monitoring-latest_data.png)

Список команд:  
`wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/
zabbix-release_6.0-4%2Bdebian11_all.deb`  
`dpkg -i zabbix-release_6.0-4+debian11_all.deb`  
`apt update`  
`sudo apt install zabbix-agent -y`  
`sudo systemctl restart zabbix-agent`  
`sudo systemctl enable zabbix-agent`  

*Добавление host-oв в web-интефейсе*  

Редактирование файла конфигурации для разрешения подключения zabbix-сервера (Server=ip):  
`sudo nano /etc/zabbix/zabbix_agentd.conf`  

*Настройка шаблона сбора данных для машин host-ов*  

`tail -f /var/log/zabbix/zabbix_agentd.log`



