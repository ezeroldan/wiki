# PHP

## Instalacion

### Debian
```bash
sudo add-apt-repository ppa:ondrej/php
sudo apt update -y
```

#### PHP 7.4
```bash
sudo apt install -y php7.4
sudo apt install -y \
    php-pear \
    php7.4-curl \
    php7.4-dev \
    php7.4-gd \
    php7.4-mbstring \
    php7.4-zip \
    php7.4-mysql \
    php7.4-xml \
    php7.4-sqlite3 \
    php7.4-mysql \
    php7.4-pgsql \
    php7.4-soap \
    php7.4-intl \
    php-xdebug
```

#### PHP 7.2
```bash
sudo apt install -y php7.2
sudo apt install -y \
    php-pear \
    php7.2-curl \
    php7.2-dev \
    php7.2-gd \
    php7.2-mbstring \
    php7.2-zip \
    php7.2-mysql \
    php7.2-xml \
    php7.2-sqlite3 
    php7.2-mysql \
    php7.2-pgsql \
    php7.2-soap \
    php7.2-intl \
    php-xdebug
```

#### PHP 5.6
```bash
sudo apt install -y php5.6
sudo apt install -y \
    php-pear \
    php5.6-curl \
    php5.6-dev \
    php5.6-gd \
    php5.6-mbstring \
    php5.6-zip \
    php5.6-mysql \
    php5.6-xml \
    php5.6-sqlite3 \
    php5.6-mysql \
    php5.6-pgsql \
    php5.6-soap
```

### Fedora
```bash
sudo dnf -y install \
    php \
    php-cli \
    php-fpm \
    php-mysqlnd \
    php-zip \
    php-devel \
    php-gd \
    php-mcrypt \
    php-mbstring \
    php-curl \
    php-xml \
    php-pear \
    php-bcmath \
    php-json \
    php-soap \
    php-intl
```

## Cambiar de Version
```bash
sudo update-alternatives --set php /usr/bin/php7.4
sudo update-alternatives --set php /usr/bin/php7.2
```

## Composer

```bash
curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
rm composer-setup.php
```

```bash
vim ~/.zshrc
export PATH="$HOME/.config/composer/vendor/bin:$PATH"
```

## Desactivar apache
```bash
sudo systemctl stop apache2
sudo systemctl disable apache2
```

## Configurar PHP

### Debian
```bash
locate php.ini
sudo vim /etc/php/7.4/fpm/php.ini
sudo vim /etc/php/7.4/cli/php.ini

sudo vim /etc/php/7.2/fpm/php.ini
sudo vim /etc/php/7.2/cli/php.ini

sudo vim /etc/php/5.6/fpm/php.ini
sudo vim /etc/php/5.6/cli/php.ini

```

### Fedora
```bash
sudo vim /etc/php.ini
```

### Configuracion
```INI
memory_limit = 512M
post_max_size = 15M
short_open_tag = On
display_errors = On
max_input_time = 900
allow_url_fopen = On
max_file_uploads = 20
max_execution_time = 900
upload_max_filesize = 15M
```

## Xdebug

### Debian
```bash
sudo apt install -y php-xdebug
sudo phpenmod -v 7.4 xdebug
sudo phpenmod -v 7.2 xdebug
```
`xdebug.show_error_trace = 1`

### Fedora

```bash
sudo dnf install php-xdebug
sudo vim /etc/php.d/15-xdebug.ini
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

## Usage
`php [options] [-f] <file> [--] [args...]`

- `-a`               Run interactively
- `-c <path>|<file>` Look for php.ini file in this directory
- `-n`               No configuration (ini) files will be used
- `-d foo[=bar]`     Define INI entry foo with value 'bar'
- `-e`               Generate extended information for debugger/profiler
- `-f <file>`        Parse and execute `<file>`.
- `-h`               This help
- `-i`               PHP information
- `-l`               Syntax check only (lint)
- `-m`               Show compiled in modules
- `-r <code>`        Run PHP `<code>` without using script tags <?..?>
- `-B <begin_code>`  Run PHP `<begin_code>` before processing input lines
- `-R <code>`        Run PHP `<code>` for every input line
- `-F <file>`        Parse and execute `<file>` for every input line
- `-E <end_code>`    Run PHP `<end_code>` after processing all input lines
- `-H`               Hide any passed arguments from external tools.
- `-S <addr>:<port>` Run with built-in web server.
- `-t <docroot>`     Specify document root `<docroot>` for built-in web server.
- `-s`               Output HTML syntax highlighted source.
- `-v`               Version number
- `-w`               Output source with stripped comments and whitespace.
- `-z <file>`        Load Zend extension `<file>`.
- `--ini`            Show configuration file names
- `--rf <name>`      Show information about function `<name>`.
- `--rc <name>`      Show information about class `<name>`.
- `--re <name>`      Show information about extension `<name>`.
- `--rz <name>`      Show information about Zend extension `<name>`.
- `--ri <name>`      Show configuration for extension `<name>`.

### Local Server
```bash
php -S localhost:8080
```