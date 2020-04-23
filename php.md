# PHP

```BASH
sudo apt install -y git
```

```BASH
sudo apt update -y && sudo apt upgrade -y
sudo add-apt-repository ppa:ondrej/php
sudo apt update -y
sudo apt install -y php7.4
sudo apt install -y php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-sqlite3 php7.4-mysql php7.4-pgsql
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