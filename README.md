# Linux Tricks & Tips

## General
```
sudo apt update -y && sudo apt-get upgrade -y
sudo apt-get install -y software-properties-common
sudo apt-get install -y git
sudo apt-get install -y curl
sudo apt-get install -y wget 
sudo apt-get install -y htop
sudo apt update
```

[Tilix](https://gnunn1.github.io/tilix-web/)

---

## exFAT
```
sudo apt-get install -y exfat-fuse exfat-utils
sudo mkdir /media/exfat
sudo mount -t exfat /dev/sdc1 /media/exfat
sudo umount /dev/sdc1
```

---

## Zsh
```
sudo apt-get update -y
sudo apt-get install -y zsh
sudo usermod -s /usr/bin/zsh $(whoami)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

sudo reboot

sudo apt-get install -y powerline fonts-powerline
sudo apt-get install -y zsh-theme-powerlevel9k
sudo apt-get install -y zsh-syntax-highlighting

echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc

nano ~/.zshrc
ZSH_THEME="agnoster"
```

---

## PHP

```
sudo apt-get update -y && sudo apt-get upgrade -y
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update -y
sudo apt-get install -y php7.4
sudo apt-get install -y php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-mcrypt php7.4-sqlite3 php7.4-mysql php7.4-pgsql
```

## Composer

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('compo	ser-setup.php');"

nano ~/.zshrc
export PATH="$HOME/.composer/vendor/bin:$PATH"
export PATH="$HOME/.config/composer/vendor/bin:$PATH"

sudo chown -R $USER ~/.composer/
```

## Laravel

```
composer global require laravel/installer
exit
```

## Valet

```
sudo apt-get install -y network-manager libnss3-tools jq xsel
composer global require cpriego/valet-linux

exit
valet install
mkdir ~/Sites
cd ~/Sites
valet park
sudo systemctl stop apache2
sudo systemctl disable apache2
```

## MariaDB & phpMyAdmin

### Instalar MariaDB
```
sudo apt-get install -y mariadb-server
sudo mysql_secure_installation
```

```
sudo systemctl status mariadb
mysql -V
mysql -u root
```

```
sudo apt-get remove -y mariadb-server
```

### Instalar phpMyAdmin
```
cd ~/Sites
composer create-project phpmyadmin/phpmyadmin
```
[phpMyAdmin](http://phpmyadmin.test)

---

## NodeJS

```
curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## Vue

```
sudo npm install -g @vue/cli
sudo npm update -g @vue/cli
```

---

## Virtualbox Guest Additions
```
sudo apt-get update -y
sudo apt-get install -y xserver-xorg-core
sudo apt-get install -y xserver-xorg-input-evdev
sudo apt-get install -y virtualbox-guest-x11
sudo reboot
```

---

## Remove a PPA

```
sudo add-apt-repository --remove ppa:PPA_Name/ppa
```

---

## Elementaryos Tweat

```
sudo add-apt-repository ppa:philip.scott/elementary-tweaks
sudo apt-get update -y
sudo apt-get install -yÂ  elementary-tweaks
```

---
## Themes & Iconos & Extesions

```
sudo apt-get update -y
sudo apt install vanilla-gnome-desktop
sudo update-alternatives --config gdm3.css
```

### .icons
- [Marwaita Icons](https://www.gnome-look.org/p/1270110/)
- [Flat Remix ICON theme](https://www.gnome-look.org/p/1012430)
- [Newaita](https://www.gnome-look.org/p/1243493)

### .themes
- [Adwaita-Color-Variants](https://www.gnome-look.org/p/1368915/)
- [Marwaita](https://www.gnome-look.org/p/1239855/)
- [Yaru-Colors](https://www.gnome-look.org/p/1299514/)

### Gnome Extensions
- [Applications Menu](https://extensions.gnome.org/extension/6/applications-menu/)
- [Removable Drive Menu](https://extensions.gnome.org/extension/7/removable-drive-menu/)
- [Places Status Indicator](https://extensions.gnome.org/extension/8/places-status-indicator/)
- [AlternateTab](https://extensions.gnome.org/extension/15/alternatetab/)
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Workspace Indicator](https://extensions.gnome.org/extension/21/workspace-indicator/)
- [Sensors](https://extensions.gnome.org/extension/82/cpu-temperature-indicator/)
- [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)
- [Caffeine](https://extensions.gnome.org/extension/517/caffeine/)
- [Clipboard Indicator](https://extensions.gnome.org/extension/779/clipboard-indicator/)
- [Remove Dropdown Arrows](https://extensions.gnome.org/extension/800/remove-dropdown-arrows/)
- [Suspend Button](https://extensions.gnome.org/extension/826/suspend-button/)
- [Refresh Wifi Connections ](https://extensions.gnome.org/extension/905/refresh-wifi-connections/)
- [Extensions](https://extensions.gnome.org/extension/1036/extensions/)
- [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/)
- [GSConnect](https://extensions.gnome.org/extension/1319/gsconnect/)
- [Desktop Icons](https://extensions.gnome.org/extension/1465/desktop-icons/)
- [Horizontal workspaces](https://extensions.gnome.org/extension/2141/horizontal-workspaces/)
- [TopIcons Plus Git](https://extensions.gnome.org/extension/2311/topicons-plus/)

