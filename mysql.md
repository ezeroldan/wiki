# MariaDB - MySQL

## Instalar MariaDB
```BASH
sudo apt install -y mariadb-server
```

## Segurizar
```BASH
sudo mysql_secure_installation
```

## Ajustar usuario ROOT

```BASH
sudo mysql -u root -p
```

```SQL
ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
FLUSH PRIVILEGES;
```

## Status
```BASH
sudo systemctl status mariadb
sudo mysql -V
```

## Desinstalar
```BASH
sudo apt remove -y mariadb-server
```

## Habilitar en boot
```BASH
sudo systemctl enable mariadb
sudo systemctl enable mysql.service
```

## Deshabilitar en boot
```BASH
sudo systemctl disable mariadb
sudo systemctl disable mysql.service
```

---

## Instalar phpMyAdmin

```BASH
cd ~/htdocs
composer create-project phpmyadmin/phpmyadmin
valet secure phpmyadmin
```

```BASH
cd ~/htdocs/phpmyadmin
cp config.sample.inc.php config.inc.php
sudo chmod 0755 config.inc.php
```

[phpMyAdmin](http://phpmyadmin.test)

---

## MySQL

### Database

#### Crear una nueva Base
```SQL
CREATE DATABASE database_name;
CREATE DATABASE IF NOT EXISTS database_name;
```

#### Listar todas las Bases
```SQL
SHOW DATABASES;
```

#### Borrar una Base
```SQL
DROP DATABASE database_name;
DROP DATABASE IF EXISTS database_name;
```

### Usuarios

#### Crear un nuevo Usuario
```SQL
CREATE USER 'database_user'@'localhost' IDENTIFIED BY 'user_password';
CREATE USER IF NOT EXISTS 'database_user'@'localhost' IDENTIFIED BY 'user_password';
```

#### Cambiar la password de un usuario
```SQL
ALTER USER 'database_user'@'localhost' IDENTIFIED BY 'new_password';
SET PASSWORD FOR 'database_user'@'localhost' = PASSWORD('new_password');
```

#### Listar todos los Usuarios
```SQL
SELECT user, host FROM mysql.user;
```

#### Borrar un Usuario
```SQL
DROP USER 'database_user'@'localhost';
```

### Privilegios

#### Otorgar permisos a un usuario
```SQL
GRANT ALL PRIVILEGES ON *.* TO 'database_user'@'localhost';
GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';
```

#### Remover permisos a un Usuario
```SQL
REVOKE ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';
```

#### Mostrar privilegios de un Usuario
```SQL
SHOW GRANTS FOR 'database_user'@'localhost';
```

```SQL
FLUSH PRIVILEGES;
```
