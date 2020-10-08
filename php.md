# PHP

## Instalacion

### Debian
```BASH
sudo add-apt-repository ppa:ondrej/php
sudo apt update -y

sudo apt install -y php7.4
sudo apt install -y php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-sqlite3 php7.4-mysql php7.4-pgsql php7.4-soap

sudo apt install -y php5.6
sudo apt install -y php-pear php5.6-curl php5.6-dev php5.6-gd php5.6-mbstring php5.6-zip php5.6-mysql php5.6-xml php5.6-sqlite3 php5.6-mysql php5.6-pgsql php5.6-soap
```
### Fedora
```bash
sudo dnf -y install php  php-cli php-fpm php-mysqlnd php-zip php-devel php-gd php-mcrypt php-mbstring php-curl php-xml php-pear php-bcmath php-json php-soap 
```

## Composer

```BASH
curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
rm composer-setup.php
```

```BASH
nano ~/.zshrc
export PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

## Laravel

```BASH
composer global require laravel/installer
```

## Valet

## Valet Linux

### Debian
```BASH
sudo apt install -y network-manager libnss3-tools jq xsel
```
### Fedora
```BASH
sudo dnf install nss-tools jq xsel
sudo dnf install php-{cli,process,mbstring,mcrypt,xml}

sudo nano /etc/selinux/config
```
`SELINUX=enforcing` => `SELINUX=permissive`
`reboot`

### Instalacion
```BASH
composer global require cpriego/valet-linux
```

### [Windows Subsystem for Linux 2 (WSL 2)](./wsl.md)
```BASH
composer global require valeryan/valet-wsl
```

### Instalar
```BASH
valet install
```

```BASH
mkdir ~/htdocs && cd ~/htdocs
valet park
```

```BASH
sudo reboot
sudo systemctl stop apache2
sudo systemctl disable apache2
```

## Xdebug  

### Debian
```BASH
sudo apt install -y php-xdebug
sudo nano /etc/php/7.4/mods-available/xdebug.ini
```
`xdebug.show_error_trace = 1`

```BASH
valet restart
```

### Fedora

```BASH
sudo dnf install php-xdebug
sudo nano /etc/php.d/15-xdebug.ini
```

```ini
zend_extension="/usr/lib64/php/modules/xdebug.so"
xdebug.remote_log="/tmp/xdebug.log"
xdebug.profiler_enable = 1
xdebug.remote_enable=on
xdebug.remote_port=9000
xdebug.remote_autostart=0
xdebug.remote_connect_back=on
xdebug.idekey=editor-xdebug
```

## NGINX Config

```BASH
sudo nano /etc/nginx/nginx.conf
valet restart
```

```
http{
    client_header_timeout 3000;
    client_body_timeout 3000;
    client_max_body_size 100M;
    fastcgi_read_timeout 3000;
    fastcgi_buffers 8 512k;
    fastcgi_buffer_size 512k;
}
```

## Configurar PHP

### Debian
```BASH
locate php.ini
sudo nano /etc/php/7.4/fpm/php.ini
sudo nano /etc/php/5.6/fpm/php.ini
```

### Fedora
```BASH
sudo nano /etc/php.ini
```

### Configuracion
```INI

[PHP]

short_open_tag = On

max_execution_time = 900

max_input_time = 900

memory_limit = 512M

error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT

display_errors = On

post_max_size = 15M

upload_max_filesize = 15M

max_file_uploads = 20

allow_url_fopen = On
```

## Compilar con Composer con PHP 5.6
```bash
php5.6 /usr/local/bin/composer install --no-dev --optimize-autoloader
```
