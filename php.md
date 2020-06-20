# PHP

```BASH
sudo apt install -y git
```

```BASH
sudo apt update -y && sudo apt upgrade -y
sudo add-apt-repository ppa:ondrej/php
sudo apt update -y
sudo apt install -y php7.4
sudo apt install -y php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-sqlite3 php7.4-mysql php7.4-pgsql php7.4-soap
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

```BASH
sudo apt install -y network-manager libnss3-tools jq xsel
composer global require cpriego/valet-linux
```

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
[xdebug](https://xdebug.org/docs/install)  

```BASH
sudo apt install -y php-xdebug
```

```BASH
sudo nano /etc/php/7.4/mods-available/xdebug.ini
```
`xdebug.show_error_trace = 1`

```BASH
valet restart
```

## NGINX Config
```BASH
sudo nano /etc/nginx/nginx.conf
valet restart
```

```
client_header_timeout 3000;
client_body_timeout 3000;
client_max_body_size 100M;
fastcgi_read_timeout 3000;
fastcgi_buffers 8 512k;
fastcgi_buffer_size 512k;
```


## Configurar PHP
```BASH
locate php.ini
sudo nano /etc/php/7.4/fpm/php.ini
```

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

[Session]
session.save_path = "/mnt/c/Users/Ezequiel/htdocs/sessions"

```