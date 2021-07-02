# Mac
- Instalar xcode developer tools

## Git & Github
git config --global user.name "Ezequiel Roldan"
git config --global user.email "ezeroldan@gmail.com"
git config --global color.ui auto

## Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## Apps
brew install curl
brew install wget
brew install htop
brew install neofetch
brew install youtube-dl

## oh my zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

### Powerlevel10k
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
p10k configure

### Plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

### Settins
vim ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

### Eliminar last login
touch ~/.hushlogin

### iTerm
#### Profiles
- Window: cols=130  rows=40

## Fira Code
brew tap homebrew/cask-fonts
brew install --cask font-fira-code

## Vim
https://vim-bootstrap.com/
brew install vim --with-python3


## NodeJS
brew install node
brew install yarn
brew install typescript

## PHP
brew install php
brew install php@7.4
brew install php@7.2

### Cambiar de version
brew unlink php
brew link php@7.4 --force --overwrite
brew link php@7.2 --force --overwrite

### Configurar
- php.ini & php-fpm.ini /usr/local/etc/php/8.0/
- To start php: brew services start php

### Composer
brew install composer
composer self-update 1.10.15

### Symfony
wget https://get.symfony.com/cli/installer -O - | bash
mv /Users/ezequiel/.symfony/bin/symfony /usr/local/bin/symfony

symfony check:requirements

## MariaDB - MySQL
brew install mariadb

### Ejecutar
mysql.server start

### Ejecutar desde inicio
brew services stop mariadb
brew services start mariadb
brew services restart mariadb

## live-sync
brew install fswatch

Validar instalacion: swatch 1.14.0
fswatch --version

```bash
#!/usr/bin/env bash

path="$HOME/geopagos"
backend_core="backend-core-mex"
source="${path}/${backend_core}"
destination="$path/$1/backend/vendor/geopagos/$backend_core"

 if [ ! -d $source ]; then
    echo "Error Core no existe: $source"
    exit 1
fi

if [ ! -d $destination ]; then
    echo "Error App no existe: $destination"
    exit 1
fi

echo "Sync: $source -> $destination"
echo

while read file; do
   echo ${file#"$source"}
   rsync -avz --delete --include='/src/***' --exclude='*' $source $destination > /dev/null
done < <(fswatch modify, create, delete $source)

```

chmod +r live-sync.sh
./live-sync.sh punto-clave

## xCode
- https://github.com/Jintin/Swimat/


## TECLADO

### Simbolos
- `⇧` Shift
- `⌥` Option (or Alt)
- `⌘` Command (or Cmd) 
- `⌃` Control (or Ctrl)

### Shorcuts
- `⇧ ⌘ .` Mostrar archivos ocultos del finder (con . en el nombre)