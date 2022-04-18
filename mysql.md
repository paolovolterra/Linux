# [MYSQL su UBUNTU](https://pen-y-fan.github.io/2021/08/08/How-to-install-MySQL-on-WSL-2-Ubuntu/)
  

sudo apt update && sudo apt upgrade # Update WSL 2 Ubuntu  
sudo apt install mysql-server # Install MySQL server  
mysql --version # Confirm installation  

su
sudo /etc/init.d/mysql start


sudo mysql_secure_installation # Secure the MySQL server  

sudo mysql # Verify MySQL is running  
	SHOW DATABASES;  
	ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root'; # Allow remote access  
	exit  
sudo update-rc.d mysql defaults # Start MySQL automatically when WSL starts   

	
# HeidiSQL can now be configured to connect to MySQL 8.0 in WSL

    Click New and give the connection a new name, e.g. MySQL-WSL2  
    Library libmysql.dll  
    Hostname / IP: localhost  
    User: root  
    Password: root  

# per installare modificare ecc; funziona
https://pen-y-fan.github.io/2021/08/08/How-to-install-MySQL-on-WSL-2-Ubuntu/

# MYSQL comandi da WSL

mysql -u root -p



# MYSQL commands

## Aggiungere ed aggiornare automaticamente una colonna timestamp in MySql
ALTER TABLE Your_Table ADD last_modified` TIMESTAMP ON UPDATE CURRENT_TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP;




SHOW COLUMNS FROM `mysql`.`user`;
SELECT `user`, `host`, authentication_string AS `password` FROM `mysql`.`user`;
CREATE USER 'pvolterr'@'%' IDENTIFIED BY '8422';
GRANT ALTER, SHOW VIEW, SHOW DATABASES, SELECT, PROCESS, EXECUTE, ALTER ROUTINE, CREATE, CREATE ROUTINE, CREATE TABLESPACE, CREATE TEMPORARY TABLES, CREATE VIEW, DELETE, DROP, EVENT, INDEX, INSERT, REFERENCES, TRIGGER, UPDATE, CREATE USER, FILE, LOCK TABLES, RELOAD, REPLICATION CLIENT, REPLICATION SLAVE, SHUTDOWN, SUPER  ON *.* TO 'pvolterr'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'pvolterr'@'%';
