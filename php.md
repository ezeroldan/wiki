# PHP

```BASH
sudo apt install -y git
```

```BASH
sudo apt update -y && sudo apt upgrade -y
sudo add-apt-repository ppa:ondrej/php
sudo apt update -y
sudo apt install -y php7.4
sudo apt install -y php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-mcrypt php7.4-sqlite3 php7.4-mysql php7.4-pgsql
```

## Composer

```BASH
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('compo	ser-setup.php');"

nano ~/.zshrc
export PATH="$HOME/.composer/vendor/bin:$PATH"
export PATH="$HOME/.config/composer/vendor/bin:$PATH"

sudo chown -R $USER ~/.composer/
```

## Laravel

```BASH
composer global require laravel/installer
exit
```

## Valet

```BASH
sudo apt install -y network-manager libnss3-tools jq xsel
composer global require cpriego/valet-linux

exit
valet install
mkdir ~/Sites
cd ~/Sites
valet park
sudo systemctl stop apache2
sudo systemctl disable apache2
```
---

# MariaDB & phpMyAdmin

## Instalar MariaDB

```BASH
sudo apt install -y mariadb-server
sudo mysql_secure_installation
```

```BASH
sudo systemctl status mariadb
mysql -V
mysql -u root
```

```BASH
sudo apt remove -y mariadb-server
```

## Instalar phpMyAdmin

```BASH
cd ~/Sites
composer create-project phpmyadmin/phpmyadmin
```

[phpMyAdmin](http://phpmyadmin.test)
