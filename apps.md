# Apps

## Debian
```BASH
sudo apt update -y && sudo apt upgrade -y

sudo apt install -y software-properties-common
sudo apt install -y curl
sudo apt install -y wget
sudo apt install -y htop
sudo apt install -y tree
sudo apt install -y zip unzip
sudo apt install -y mlocate
sudo apt install -y neofetch
sudo apt install -y cmatrix

sudo apt install -y vlc
sudo apt install -y filezilla
sudo apt install -y spotify-client
sudo apt install -y thunderbird
sudo apt install -y thunderbird-locale-es-ar
sudo apt install -y inkscape
sudo apt install -y gnome-sushi
```

## Fedora
```BASH
sudo dnf update

sudo rpm -Uvh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo rpm -Uvh http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

sudo dnf install -y htop
sudo dnf install -y neofetch
sudo dnf install -y cmatrix

sudo dnf install -y vlc
sudo dnf install -y inkscape
sudo dnf install -y filezilla
sudo dnf install -y thunderbird
```

## Flatpak
```BASH
flatpak install flathub com.spotify.Client
flatpak install flathub com.notepadqq.Notepadqq
```

## Microsoft TrueType Fonts
```BASH
sudo add-apt-repository multiverse
sudo apt update && sudo apt install ttf-mscorefonts-installer
sudo fc-cache -f -v

sudo apt install –reinstall ttf-mscorefonts-installer
```

[PhotoGIMP](https://github.com/Diolinux/PhotoGIMP)

## Drivers
[Asus Q325UA](https://www.asus.com/supportonly/Q325UA/HelpDesk_Download/)  
