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

sudo vim /etc/php/7.2/mods-available/xdebug.ini
```

```ini
zend_extension="/usr/lib/php/20190902/xdebug.so"
xdebug.remote_log="/tmp/xdebug.log"
xdebug.profiler_enable = 1
xdebug.remote_enable=on
xdebug.remote_port=9000
xdebug.remote_autostart=0
xdebug.remote_connect_back=on
xdebug.idekey=editor-xdebug
xdebug.show_error_trace = 1
```

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

## bins

### php
PHP Command Line Interface CLI

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
- `-S <addr>:<port>` Run with built-in web server. `php -S localhost:8080`
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

## phpize
Prepare PHP extension for compiling.
- `--clean` Remove all created files
- `--help` Prints usage information
- `--version` `-v` Prints API version information

## php-config
Obtaining information about installed PHP configuration.
- `--prefix` Directory prefix where PHP is installed, e.g. /usr/local
- `--includes` List of -I options with all include files
- `--ldflags` LD Flags which PHP was compiled with
- `--libs` Extra libraries which PHP was compiled with
- `--man-dir` The directory prefix where the manpages is installed
- `--extension-dir` Directory where extensions are searched by default
- `--include-dir` Directory prefix where header files are installed by default
- `--php-binary` Full path to php CLI or CGI binary
- `--php-sapis` Show all SAPI modules installed on the Debian system
- `--configure-options` Configure options to recreate configuration of current PHP installation

## phar
The PHAR file format provides a way to put entire PHP applications into a single file called a "phar" (PHP Archive)

- `add` Add entries to a PHAR package.
    - `-f` file        Specifies the phar file to work on. (Required)
       ...            Any  number  of  input  files and directories. If -i is in use then ONLY files and matching the given regular expression are being packed. If -x is given then files matching that regular expression are NOT being packed.
    - `-a` alias       Provide an alias name for the phar file. (Optional)
    - `-c` algo        Compression algorithm (see COMPRESSION ) (Optional)
    - `-i` regex       Specifies a regular expression for input files. (Optional)
    - `-l` level       Number of preceding subdirectories to strip from file entries (Optional)
    - `-x` regex       Regular expression for input files to exclude. (Optional)
- `compress` Compress or uncompress all files or a selected entry.
    - `-c` algo        Compression algorithm (see COMPRESSION ) (Required)
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-e` entry       Name of entry to work on (must include PHAR internal directory name if any). (Optional)
- `delete` Delete entry from a PHAR archive
    - `-e` entry       Name of entry to work on (must include PHAR internal directory name if any). (Required)
    - `-f` file        Specifies the phar file to work on. (Required)s
- `extract` Extract a PHAR package to a directory.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-i` regex       Specifies a regular expression for input files. (Optional)
    - `-x` regex       Regular expression for input files to exclude. (Optional)
    ...            Directory to extract to (defaults to '.').
- `help ...`
- `help-list` Lists available commands.
- `info` Get information about a PHAR package. By using -k it is possible to return a single value.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-k` index       Subscription index to work on. (Optional)
- `list` List contents of a PHAR archive.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-i` regex       Specifies a regular expression for input files. (Optional)
    - `-x` regex       Regular expression for input files to exclude. (Optional)
- `meta-del` Delete meta information of a PHAR entry or a PHAR package. If -k is given then the metadata is expected to be an array and the given index is being deleted. If something was deleted the return value is 0 otherwise it is 1.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-e` entry       Name of entry to work on (must include PHAR internal directory name if any). (Optional)
    - `-k` index       Subscription index to work on. (Optional)
- `meta-get` Get meta information of a PHAR entry or a PHAR package in serialized from. If no output file is specified for meta data then stdout is being used.  You can also specify a particular  index using  -k. In that case the metadata is expected to be an array and the value of the given index is returned using echo rather than using serialize. If that index does not exist or no metadata is present then the return value is 1.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-e` entry       Name of entry to work on (must include PHAR internal directory name if any). (Optional)
    - `-k` index       Subscription index to work on. (Optional)
- `meta-set` Set meta data of a PHAR entry or a PHAR package using serialized input. If no input file is specified for meta data then stdin is being used. You can also specify a particular index  using k.  In that case the metadata is expected to be an array and the value of the given index is being set.  If the metadata is not present or empty a new array will be created.  If the metadata is present and a flat value then the return value is 1. Also using -k the input is been taken directly rather then being serialized.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-m` meta        Meta data to store with entry (serialized php data). (Required)
    - `-e` entry       Name of entry to work on (must include PHAR internal directory name if any). (Optional)
    - `-k` index       Subscription index to work on. (Optional)
- `pack` Pack files into a PHAR archive.
    - `-f` file        Specifies the phar file to work on. (Required)
    ...            Any  number  of  input  files and directories. If -i is in use then ONLY files and matching the given regular expression are being packed. If -x is given then files matching that regular expression are NOT being packed.
    - `-a` alias       Provide an alias name for the phar file. (Optional)
    - `-b` bang        Hash-bang line to start the archive (e.g. #!/usr/bin/php).  The hash mark itself '#!' and the newline character are optional. (Optional)
    - `-c` algo        Compression algorithm (see COMPRESSION ) (Optional)
    - `-h` hash        Selects the hash algorithm (see HASH ) (Optional)
    - `-i` regex       Specifies a regular expression for input files. (Optional)
    - `-l` level       Number of preceding subdirectories to strip from file entries (Optional)
    - `-p` loader      Location of PHP_Archive class file (pear list-files PHP_Archive).You can use '0' or '1' to locate it automatically using the mentioned pear command. When using '0' the  command  does  not  error out when the class file cannot be located. This switch also adds some code around the stub so that class PHP_Archive gets registered as phar:// stream wrapper if necessary. And finally this switch will add the file phar.inc from this package and load it to ensure class Phar is present. (Optional)
    - `-s` stub        Select the stub file. (Optional)
    - `-x` regex       Regular expression for input files to exclude. (Optional)
    - `-y` key         Private key for OpenSSL signing. (Optional)
- `sign` Set signature hash algorithm.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-h` hash        Selects the hash algorithm (see HASH ) (Required)
    - `-y` key         Private key for OpenSSL signing. (Optional)
- `stub-get` Get the stub of a PHAR file. If no output file is specified as stub then stdout is being used.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-s` stub        Select the stub file. (Optional)
- `stub-set` Set the stub of a PHAR file. If no input file is specified as stub then stdin is being used.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-b` bang        Hash-bang line to start the archive (e.g. #!/usr/bin/php).  The hash mark itself '#!' and the newline character are optional. (Optional)
    - `-p` loader      Location of PHP_Archive class file (pear list-files PHP_Archive).You can use '0' or '1' to locate it automatically using the mentioned pear command. When using '0' the  command  does  not  error out when the class file cannot be located. This switch also adds some code around the stub so that class PHP_Archive gets registered as phar:// stream wrapper if necessary. And finally this switch will add the file phar.inc from this package and load it to ensure class Phar is present. (Optional)
    - `-s` stub        Select the stub file. (Optional)
- `tree` Get a directory tree for a PHAR archive.
    - `-f` file        Specifies the phar file to work on. (Required)
    - `-i` regex       Specifies a regular expression for input files. (Optional)
    - `-x` regex       Regular expression for input files to exclude. (Optional)
- `version` Get information about the PHAR environment and the tool version. (Optional)

### Composer
- `require` Adds required packages to your composer.json and installs them.
- `remove` Removes a package from the require or require-dev.
- `u` `update` `upgrade` Upgrades your dependencies to the latest version according to composer.json, and updates the composer.lock file.
- `run` `run-script` Runs the scripts defined in composer.json.
- `about` Shows the short information about Composer.
- `archive` Creates an archive of this composer package.
- `browse` Opens the package's repository URL or homepage in your browser.
- `cc` Clears composer's internal package cache.
- `check-platform-reqs- ` Check that platform requirements are satisfied.
- `clear-cache` `clearcache` Clears composer's internal package cache.
- `config` Sets config options.
- `create-project` Creates new project from a package into given directory.
- `depends` Shows which packages cause the given package to be installed.
- `diagnose` Diagnoses the system to identify common errors.
- `dump-autoload` `dumpautoload` Dumps the autoloader.
- `exec` Executes a vendored binary/script.
- `fund` Discover how to help fund the maintenance of your dependencies.
- `global` Allows running commands in the global composer dir ($COMPOSER_HOME).
- `help` Displays help for a command
- `home` Opens the package's repository URL or homepage in your browser.
- `i` `install` Installs the project dependencies
- `info` `show` Shows information about packages.
- `init` Creates a basic composer.json file in current directory.
- `licenses` Shows information about licenses of dependencies.
- `list` Lists commands
- `outdated` Shows a list of installed packages that have updates available, including their latest version.
- `prohibits` Shows which packages prevent the given package from being installed.
- `search` Searches for packages.
- `self-update` `selfupdate` Updates composer.phar to the latest version.
- `status` Shows a list of locally modified packages.
- `suggests` Shows package suggestions.
- `validate` Validates a composer.json and composer.lock.
- `why` `why-not` Shows which packages cause the given package to be installed.

