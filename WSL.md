# Windows Subsystem for Linux 2 (WSL 2)

[Learn how to install WSL 2](https://www.youtube.com/watch?v=ilKQHAFeQR0)  

## Windows Features
- Virtual Machine Platform
- Windows Subsystem for Linux

## Fuentes
[DejaVuSansMono](https://github.com/ryanoasis/nerd-fonts/releases/download/v1.2.0/DejaVuSansMono.zip)  
`DejaVu Sans Mono for Powerline Nerd Font Complete Mono Windows Compatible.ttf`  

## Terminal

### Chocolatey
```BASH
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```
### Terminal
```BASH
choco install microsoft-windows-terminal
```

[settings.json](https://github.com/microsoft/terminal/blob/master/doc/cascadia/SettingsSchema.md)  

```JSON
{
    "copyOnSelect": true,
    "theme": "dark",
    "launchMode": "maximized",
    "profiles": {
        "defaults": {
            "fontFace": "DejaVu Sans Mono for Powerline",
            "fontSize": 10,
            "useAcrylic": false,
            "acrylicOpacity": 0.8
        },
        "list": [
            {

            }
        ]
    }
}
```
## Instalar Pogramas
1. [ZSH](./zsh.md)
2. [Git](./git.md)
3. [PHP](./PHP.md)
4. [MySQL](./mysql.md)
5. [NodeJS](./nodejs.php)

## Acrylic Setup (Windows)

### Instalar
[Acrylic DNS Proxy](http://mayakron.altervista.org/wikibase/show.php?id=AcrylicHome)
[Windows 10 Configuration](https://mayakron.altervista.org/support/acrylic/Windows10Configuration.htm)

### Configurar
`Control Panel\Network and Internet\Network Connections`  

#### Internet Protocol Version 4 (TCP/IPv4)
`127.0.0.1`  
`8.8.8.8`  

#### Internet Protocol Version 6 (TCP/IPv6)
`::1`  
`2001:4860:4860::8888`  

1. Editar **Acrylic Host File**
2. `127.0.0.1 *.test`
3. Stop Acrylic Service
4. Start Acrylic Service

## Valet
```BASH
composer global require valeryan/valet-wsl
```

## Symbolic Link
```BASH
ln -s /mnt/c/Users/Ezequiel/htdocs /home/ezequiel/htdocs
```

## Resolver error de DNS
```BASH
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
echo "nameserver 8.8.8.8" | sudo tee /etc/resolvconf/resolv.conf.d/base > /dev/null
```
## MySql
```BASH
sudo usermod -d /var/lib/mysql/ mysql
sudo service mysql start
sudo mysql
```

### Instalar phpMyAdmin

```BASH
cd ~/htdocs
mkdir phpmyadmin
cd phpmyadmin
composer create-project phpmyadmin/phpmyadmin
ln -s /mnt/c/Users/Ezequiel/htdocs/phpmyadmin/phpmyadmin /mnt/c/Users/Ezequiel/htdocs/phpmyadmin/pma
valet park
```
## Secure https

```BASH
valet secure folder
```

Ejecutar:  
`C:/tools/valet/certs/install_certs.cmd`

## Cron Jobs
Run `sudo crontab -e`  

```BASH
*/5 * * * * php /mnt/c/username/Projects/folder/artisan schedule:run >> /dev/null 2>&1
```

