# Mac
- xcode 
- developer tools

## Git & Github
- `git config --global user.name "Ezequiel Roldan"`
- `git config --global user.email "ezeroldan@gmail.com"`
- `git config --global color.ui auto`

## Homebrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Apps
- `brew install curl`
- `brew install wget`
- `brew install htop`
- `brew install neofetch`
- `brew install youtube-dl`

## oh my zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### Powerlevel10k
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

`p10k configure`

### Plugins
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### Settins
`nano ~/.zshrc`
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

### Eliminar last login
```bash
touch ~/.hushlogin
```

### iTerm
#### Profiles
- Window: cols=130  rows=40

## Fira Code
- `brew tap homebrew/cask-fonts`
- `brew install --cask font-fira-code`

## Nano
- `brew install nano`
- `touch ~/.nanorc && nano ~/.nanorc`
- `sudo nano /etc/nanorc`

```bash
set mouse
set nowrap
set smooth
set autoindent
set tabsize 4
set tabstospaces
set linenumbers

include /usr/local/share/nano/*.nanorc

```

## Vim
- https://macvim-dev.github.io/macvim/
- https://vim-bootstrap.com/
- `brew install vim --with-python3`

## NodeJS
- `brew install node`
- `brew install yarn`
- `brew install typescript`

## PHP
- `brew install php`
- `brew install php@7.4`
- `brew install php@7.2`

### Cambiar de version
- `brew unlink php`
- `brew link php@7.4 --force --overwrite`
- `brew link php@7.2 --force --overwrite`

### Configurar
- php.ini & php-fpm.ini /usr/local/etc/php/8.0/
- To start php: brew services start php

### Composer
- `brew install composer`
- `composer self-update 1.10.15`

### Symfony
- `wget https://get.symfony.com/cli/installer -O - | bash`
- `mv /Users/ezequiel/.symfony/bin/symfony /usr/local/bin/symfony`
- `symfony check:requirements`

### xdebug
- `pecl install xdebug`
- `extension=xdebug.so` to `php.ini`

## MariaDB - MySQL
- `brew install mariadb`

### Ejecutar
- `mysql.server start`

### Ejecutar desde inicio
- `brew services stop mariadb`
- `brew services start mariadb`
- `brew services restart mariadb`

## xCode
- https://github.com/Jintin/Swimat/
- https://developer.apple.com/sf-symbols/

## Otros
- https://github.com/kmikiy/SpotMenu#easy-install

## TECLADO

### Simbolos
- `⇧` Shift
- `⌥` Option (or Alt)
- `⌘` Command (or Cmd) 
- `⌃` Control (or Ctrl)

### Shorcuts
- `⇧ ⌘ .` Mostrar archivos ocultos del finder (con . en el nombre)