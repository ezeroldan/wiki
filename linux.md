# Apps

## Debian
```bash
sudo apt update -y && sudo apt upgrade -y

sudo apt install -y software-properties-common
sudo apt install -y vim
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
```bash
sudo dnf update

flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

sudo dnf copr enable kwizart/fedy
sudo dnf install fedy -y

sudo dnf install -y vim
sudo dnf install -y htop
sudo dnf install -y neofetch
sudo dnf install -y cmatrix

sudo dnf install -y vlc
sudo dnf install -y inkscape
sudo dnf install -y filezilla
sudo dnf install -y thunderbird
```

## Flatpak
```bash
flatpak install flathub com.spotify.Client
flatpak install flathub com.notepadqq.Notepadqq
```

## Microsoft TrueType Fonts
```bash
sudo add-apt-repository multiverse
sudo apt update && sudo apt install ttf-mscorefonts-installer
sudo fc-cache -f -v

sudo apt install –reinstall ttf-mscorefonts-installer
```

[PhotoGIMP](https://github.com/Diolinux/PhotoGIMP)

## Drivers
[Asus Q325UA](https://www.asus.com/supportonly/Q325UA/HelpDesk_Download/)  

# Gnome

## Gnome Tool
```bash
sudo apt install -y gnome-tweak-tool
sudo apt install -y chrome-gnome-shell
mkdir .icons
mkdir .themes

sudo apt install gnome-session
sudo update-alternatives --config gdm3-theme.gresource
```

## Themes
- [Yaru-Colors](https://www.gnome-look.org/p/1299514/)  
- [Adwaita-Slim](https://github.com/archbyte/Adwaita-Slim)
- [Newaita](https://www.gnome-look.org/p/1243493/)

## Fonts
- [Ubuntu](https://fonts.google.com/specimen/Ubuntu)
- [FiraCode](https://github.com/tonsky/FiraCode)
- [Open Sans](https://fonts.google.com/specimen/Open+Sans)

## Extensions
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Desktop Icons NG](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)
- [Multi Monitors](https://extensions.gnome.org/extension/921/multi-monitors-add-on/)
- [Animation Tweaks](https://extensions.gnome.org/extension/1680/animation-tweaks/)

### Topbar
- [AppIndicator and KStatusNotifierItem Support](https://extensions.gnome.org/extension/615/appindicator-support/)
- [Apt Update Indicator](https://extensions.gnome.org/extension/1139/apt-update-indicator/)
- [Clipboard Indicator](https://extensions.gnome.org/extension/779/clipboard-indicator/)
- [Caffeine](https://extensions.gnome.org/extension/517/caffeine/)
- [EasyScreenCast](https://extensions.gnome.org/extension/690/easyscreencast/)
- [Frippery Move Clock ](https://extensions.gnome.org/extension/2/move-clock/)
- [Mpris Indicator Button](https://extensions.gnome.org/extension/1379/mpris-indicator-button/)
- [NetSpeed](https://extensions.gnome.org/extension/104/netspeed/)
- [Panel OSD](https://extensions.gnome.org/extension/708/panel-osd/)
- [Removable Drive Menu](https://extensions.gnome.org/extension/7/removable-drive-menu/)
- [Screenshot Tool](https://extensions.gnome.org/extension/1112/screenshot-tool/)
- [Sound Input & Output Device Chooser](https://extensions.gnome.org/extension/906/sound-output-device-chooser/)
- [Transparent Top Bar](https://extensions.gnome.org/extension/1708/transparent-top-bar/)
- [Unite](https://extensions.gnome.org/extension/1287/unite/)

### Dock
- [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)  
- [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/)  
