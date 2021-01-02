# MariaDB - MySQL

## Instalar MariaDB

### Debian
```bash
sudo apt install -y mariadb-server
```

### Fedora
```bash
sudo dnf install mariadb mariadb-server
sudo systemctl start mariadb
```

## Segurizar
```bash
sudo mysql_secure_installation
```

## Ajustar usuario ROOT

```bash
sudo mysql -u root -p
```

```sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
FLUSH PRIVILEGES;
```

## Habilitar en boot
```bash
sudo systemctl enable mariadb
sudo systemctl enable mysql.service
```

## Deshabilitar en boot
```bash
sudo systemctl disable mariadb
sudo systemctl disable mysql.service
```

---

## Instalar phpMyAdmin

```bash
cd ~/htdocs
composer create-project phpmyadmin/phpmyadmin
valet secure phpmyadmin
```

```bash
cd ~/htdocs/phpmyadmin
cp config.sample.inc.php config.inc.php
sudo chmod 0755 config.inc.php
```

[phpMyAdmin](http://phpmyadmin.test)

---

## MySQL

### Database

#### Crear una nueva Base
```sql
CREATE DATABASE database_name;
CREATE DATABASE IF NOT EXISTS database_name;
```

#### Listar todas las Bases
```sql
SHOW DATABASES;
```

#### Borrar una Base
```sql
DROP DATABASE database_name;
DROP DATABASE IF EXISTS database_name;
```

### Backups

#### Importar
```sql
mysql -u root -p -h localhost DB_NAME < filename.sql
```

#### Exportar
```sql
mysqldump -u root -p DB_NAME > filename.sql
```

### Usuarios

#### Crear un nuevo Usuario
```sql
CREATE USER 'database_user'@'localhost' IDENTIFIED BY 'user_password';
CREATE USER IF NOT EXISTS 'database_user'@'localhost' IDENTIFIED BY 'user_password';
```

#### Cambiar la password de un usuario
```sql
ALTER USER 'database_user'@'localhost' IDENTIFIED BY 'new_password';
SET PASSWORD FOR 'database_user'@'localhost' = PASSWORD('new_password');
```

#### Listar todos los Usuarios
```sql
SELECT user, host FROM mysql.user;
```

#### Borrar un Usuario
```sql
DROP USER 'database_user'@'localhost';
```

### Privilegios

#### Otorgar permisos a un usuario
```sql
GRANT ALL PRIVILEGES ON *.* TO 'database_user'@'localhost';
GRANT ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';
```

#### Remover permisos a un Usuario
```sql
REVOKE ALL PRIVILEGES ON database_name.* TO 'database_user'@'localhost';
```

#### Mostrar privilegios de un Usuario
```sql
SHOW GRANTS FOR 'database_user'@'localhost';
```

```sql
FLUSH PRIVILEGES;
```
