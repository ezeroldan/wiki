# Gnome

## Gnome Tool
```BASH
sudo apt install -y gnome-tweak-tool
sudo apt install -y chrome-gnome-shell
mkdir .icons
mkdir .themes

sudo apt install gnome-session
sudo update-alternatives --config gdm3-theme.gresource
```

## Themes
- [Yaru-Colors](https://www.gnome-look.org/p/1299514/)  
- [NewAdwaitaSlimDark](https://github.com/ch4rcoil/NewAdwaitaSlimDark)

## Fonts
- [Open Sans](https://fonts.google.com/specimen/Open+Sans)  
- [FiraCode](https://github.com/tonsky/FiraCode)  

## Extensions
- [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
- [Desktop Icons NG](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)

### Topbar
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

### Dock
- [Dash to Dock](https://extensions.gnome.org/extension/307/dash-to-dock/)  
- [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/)  



## Touchpad Gestures 
[Fusuma](https://github.com/iberianpig/fusuma)

```bash
sudo gpasswd -a $USER input
sudo reboot
sudo apt install libinput-tools -y
sudo apt install xdotool -y
sudo apt install ruby -y
sudo gem install fusuma
mkdir -p ~/.config/fusuma
nano ~/.config/fusuma/config.yml
```

```yaml
swipe:
  3:
    left:
      command: "xdotool key alt+Right" # History forward
    right:
      command: "xdotool key alt+Left" # History back
    up:
      command: "xdotool key super" # Activity
    down:
      command: "xdotool key super+a" # Aplicaciones
  4:
    left:
      command: "xdotool key ctrl+alt+Down" # Switch to next workspace
    right:
      command: "xdotool key ctrl+alt+Up" # Switch to previous workspace
    up:
      command: "xdotool key ctrl+alt+Down" # Switch to next workspace
    down:
      command: "xdotool key ctrl+alt+Up" # Switch to previous workspace
pinch:
  in:
    command: "xdotool keydown ctrl click 4 keyup ctrl" # Zoom in
  out:
    command: "xdotool keydown ctrl click 5 keyup ctrl" # Zoom out
```

```bash
gnome-session-properties
/usr/local/bin/fusuma -d
```



