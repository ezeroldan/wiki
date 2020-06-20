# Zsh
```BASH
sudo apt update -y
sudo apt install -y zsh
sudo usermod -s /usr/bin/zsh $(whoami)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

sudo reboot

sudo apt install -y powerline fonts-powerline
sudo apt install -y zsh-theme-powerlevel9k
sudo apt install -y zsh-syntax-highlighting

echo "source /usr/share/powerlevel9k/powerlevel9k.zsh-theme" >> ~/.zshrc
echo "source /usr/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ~/.zshrc

nano ~/.zshrc
ZSH_THEME="agnoster"
```
